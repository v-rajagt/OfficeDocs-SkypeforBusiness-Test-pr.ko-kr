﻿---
title: 'Lync Server 2013: SIP 트렁크를 구현하는 방법'
TOCTitle: SIP 트렁크를 구현하는 방법
ms:assetid: 273a22b1-8a4c-4187-acf8-c57d5c6598ce
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425743(v=OCS.15)
ms:contentKeyID: 49303108
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 SIP 트렁크를 구현하는 방법

 

_**마지막으로 수정된 항목:** 2013-03-18_

SIP 트렁크를 구현하려면 Lync Server 2013 클라이언트와 서비스 공급자 간의 통신 세션용 프록시로 작동하고 필요한 경우 미디어 코드를 변환하는 중재 서버를 통해 연결을 라우팅해야 합니다.

각 중재 서버에는 내부 네트워크 인터페이스와 외부 네트워크 인터페이스가 있습니다. 내부 인터페이스는 프런트 엔드 서버에 연결됩니다, 외부 인터페이스는 주로 중재 서버를 공중 전화망(PSTN) 게이트웨이 또는 IP-PBX에 연결하는 데 사용되어 왔기 때문에 게이트웨이 인터페이스라고 합니다. SIP 트렁크를 구현하려면 중재 서버의 외부 인터페이스를 ITSP의 외부 에지 구성 요소에 연결합니다.


> [!NOTE]
> ITSP의 외부 에지 구성 요소는 SBC(세션 경계 컨트롤러), 라우터 또는 게이트웨이일 수 있습니다.



중재 서버에 대한 자세한 내용은 [Lync Server 2013의 중재 서버 구성 요소](lync-server-2013-mediation-server-component.md)를 참고하세요.

## 중앙 집중식 SIP 트렁크와 분산형 SIP 트렁크

*중앙 집중식* SIP 트렁크는 분기 사이트 트래픽을 포함하여 모든 VoIP(Voice over Internet Protocol) 트래픽을 중앙 사이트를 통해 라우팅합니다. 중앙 집중식 배포 모델은 단순하고 경제적이므로 일반적으로 Lync Server 2013을 사용하여 SIP 트렁크를 구현하는 데 권장됩니다.

*분산형* SIP 트렁크는 하나 이상의 분기 사이트에 로컬 SIP 트렁크를 구현하는 배포 모델입니다. 이 경우 VoIP 트래픽은 중앙 사이트를 통과하지 않고 분기 사이트에서 서비스 공급자로 직접 라우팅됩니다.

분산형 SIP 트렁크는 다음과 같은 경우에만 필요합니다.

  - 분기 사이트에 지속 가능한 전화 연결이 필요한 경우(예: WAN이 다운된 경우). 이 요구 사항은 각 분기 사이트에 대해 분석해야 합니다. 분기에 따라 중복성 및 장애 조치가 필요할 수도 있고 그렇지 않을 수도 있습니다.

  - 두 중앙 사이트 간에 복구가 필요한 경우. 각 SIP 트렁크가 각 중앙 사이트에서 종료되어야 합니다. 예를 들어 Dublin 및 Tukwila 중앙 사이트가 있고 두 사이트에서 모두 한 사이트의 SIP 트렁크만 사용하는 경우 트렁크가 다운되면 다른 사이트의 사용자가 PSTN 전화를 사용할 수 없습니다.

  - 분기 사이트와 중앙 사이트가 서로 다른 국가/지역에 있는 경우. 호환성 및 규정 준수를 위해 국가/지역당 하나 이상의 SIP 트렁크가 필요합니다. 예를 들어 유럽 연합의 경우 중앙 지점에서 로컬로 종료되지 않은 통신은 국가/지역을 벗어날 수 없습니다.

사이트의 지리적 위치 및 엔터프라이즈 내에서 예상되는 트래픽 양에 따라 일부 사용자를 중앙 SIP 트렁크를 통해 라우팅하지 않거나 일부 사용자를 해당 분기 사이트의 SIP 트렁크를 통해 라우팅할 수 있습니다. 다음 질문에 대한 대답을 통해 요구 사항을 분석할 수 있습니다.

  - 각 사이트의 규모가 어느 정도입니까? 즉, Enterprise Voice를 사용하도록 설정된 사용자가 몇 명입니까?

  - 각 사이트에서 대부분의 전화 통화가 이루어지는 DID(Direct Inward Dialing) 번호는 몇 번입니까?

중앙 집중식 SIP 트렁크를 배포할지, 분산형 SIP 트렁크를 배포할지를 결정하려면 비용 관련 이점을 분석해야 합니다. 경우에 따라 분산형 배포 모델이 필요하지 않은 경우에도 이 모델이 훨씬 이익인 경우가 있을 수 있습니다. 완전히 중앙화된 배포에서는 모든 분기 사이트 트래픽이 WAN 링크를 통해 라우팅됩니다. WAN 링크에 필요한 대역폭에 대한 비용을 지불하는 대신 분산형 SIP 트렁크를 사용할 수 있습니다. 예를 들어 중앙 사이트와 페더레이션된 분기 사이트에 Standard Edition 서버를 배포하거나 소규모 게이트웨이와 함께 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버를 배포할 수 있습니다.


> [!NOTE]
> 분산형 SIP 트렁크를 사용하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-branch-site-sip-trunking.md">Lync Server 2013의 분기 사이트 SIP 트렁크</A>를 참고하세요.



## 지원되는 SIP 트렁크 연결 유형

Lync Server에서는 SIP 트렁크에 대해 다음과 같은 연결 유형을 지원합니다.

  - MPLS(Multiprotocol Label Switching)는 하나의 네트워크 노드에서 다음 네트워크 노드로 데이터를 전달하는 개인 네트워크입니다. MPLS 네트워크의 대역폭은 다른 구독자와 공유되며, 각 데이터 패킷에는 구독자 간에 데이터를 구별하는 레이블이 할당됩니다. 이 연결 유형에는 VPN(가상 사설망)이 필요하지 않습니다. 그러나 VoIP 트래픽이 우선적으로 적용되지 않는 경우 과도한 IP 트래픽으로 인해 VoIP 작업이 방해를 받을 수 있다는 단점이 있습니다.

  - 다른 트래픽(예: 임대된 광 케이블 연결 또는 T1 회선)이 없는 개인 연결은 일반적으로 가장 안정적이고 안전한 연결 유형입니다. 이 연결 유형은 최고의 통화 전달 용량을 제공하지만 일반적으로 가장 비싸며, VPN이 필요하지 않습니다. 개인 연결은 통화량이 많거나 보안 및 사용 가능성 요구 사항이 엄격한 조직에 적합합니다.

  - 인터넷은 비용이 가장 저렴한 연결 유형이지만 안정성도 가장 낮습니다. 인터넷 연결은 VPN이 필요한 유일한 Lync Server SIP 트렁크 연결 유형입니다.

## 연결 유형 선택

회사에 가장 적절한 SIP 트렁크 연결 유형은 요구 사항 및 예산에 따라 결정됩니다.

  - 중규모 또는 대규모 기업에서는 일반적으로 MPLS 네트워크가 가장 큰 가치를 제공합니다. MPLS 네트워크는 전문화된 개인 네트워크보다 저렴한 비용으로 필요한 대역폭을 제공할 수 있습니다.

  - 대기업에는 전용 광 케이블, T1, T3 또는 그 이상의 연결(유럽 연합의 경우 E1, E3 이상)이 필요할 수 있습니다.

  - 소규모 기업이나 통화량이 적은 분기 사이트의 경우에는 인터넷을 통한 SIP 트렁크가 가장 적절할 수 있습니다. 이 연결 유형은 중규모 또는 대규모 사이트에는 권장되지 않습니다.

## 대역폭 요구 사항

구현에 필요한 대역폭 양은 통화 용량(지원할 수 있어야 하는 동시 통화 수)에 따라 결정됩니다. 비용을 지불하는 최대 용량을 충분히 활용할 수 있도록 대역폭 사용 가능성을 고려해야 합니다. 다음 수식을 사용하여 SIP 트렁크 최대 대역폭 요구 사항을 계산할 수 있습니다.

SIP 트렁크 최대 대역폭 = 최대 동시 통화 수 x (64kbps + 헤더 크기)


> [!NOTE]
> 헤더 크기는 20바이트가 최대값입니다.



## 코덱 지원

Lync Server 2013에서는 다음과 같은 코덱만 지원합니다.

  - G.711 a-law(주로 북미 이외의 다른 지역에서 사용)

  - G.711 μ-law(북미에서 사용)

## 인터넷 전화 통신 서비스 공급자

SIP 트렁크 연결의 서비스 공급자 쪽을 구현하는 방법은 ITSP에 따라 다릅니다. 배포 정보에 대해서는 서비스 공급자에 문의하세요. 인증된 SIP 트렁크 서비스 공급자 목록은 [Microsoft Unified Communications Open Interoperability Program 웹 사이트(](http://go.microsoft.com/fwlink/?linkid=287029))를 참고하세요.

Microsoft 인증 SIP 트렁크 공급자에 대한 자세한 내용은 Microsoft 담당자에게 문의하세요.


> [!IMPORTANT]
> Microsoft 인증 서비스 공급자를 사용하여 ITSP가 SIP 트렁크를 트래버스하는 모든 기능(예: 세션 설정 및 관리와 모든 확장된 VoIP 서비스 지원)을 지원하도록 해야 합니다. Microsoft 기술 지원은 인증되지 않은 공급자를 사용하는 구성으로 확장되지 않습니다. 현재 SIP 트렁크에 대해 인증되지 않은 인터넷 서비스 공급자를 사용하는 경우 해당 공급자를 계속해서 ISP로 사용하고 SIP 트렁크에 대해서는 Microsoft 인증 공급자를 사용하도록 선택할 수 있습니다.

