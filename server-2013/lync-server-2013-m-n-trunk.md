﻿---
title: 'Lync Server 2013: M:N 트렁크'
TOCTitle: M:N 트렁크
ms:assetid: dc4c5d66-297c-48a5-91b9-b9b8ce44a6e0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398971(v=OCS.15)
ms:contentKeyID: 49305239
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 M:N 트렁크

 

_**마지막으로 수정된 항목:** 2012-10-01_

Lync Server 2013에서는 이전 릴리스의 통화 라우팅 용도로 트렁크 정의 면에서 향상된 유연성을 지원합니다. 트렁크는 게이트웨이와 수신 대기 포트 번호를 사용한 중재 서버와 수신 대기 포트 번호 간의 논리적 연결입니다. 이는 몇 가지 의미를 함축합니다. 중재 서버에 동일한 게이트웨이에 대한 여러 트렁크가 있을 수 있으며, 중재 서버에 다양한 게이트웨이에 대한 여러 트렁크가 있을 수 있습니다. 거꾸로 게이트웨이에 다양한 중재 서버에 대한 여러 트렁크가 있을 수 있습니다.

토폴로지 작성기를 사용하여 Lync 토폴로지에 게이트웨이를 추가하는 경우에도 루트 트렁크를 만들어야 합니다. 지정된 중재 서버에서 처리할 수 있는 게이트웨이 수는 사용량이 가장 많은 시간 동안 서버의 처리 용량에 따라 달라집니다. 지원 가능성 설명서의 [Lync Server 2013에서 지원되는 하드웨어](lync-server-2013-supported-hardware.md)에 설명된 대로 Lync Server 2013에 대한 최소 하드웨어 요구 사항을 초과하는 하드웨어에 중재 서버를 배포하는 경우 독립 실행형 중재 서버에서 처리할 수 있는 예상 활성 통화(바이패스 없음) 수는 약 1000통입니다. 이러한 사양을 충족하는 하드웨어에 배포될 경우 중재 서버는 코드 변환을 수행하지만 게이트웨이가 미디어 바이패스를 지원하지 않는 경우에도 여러 게이트웨이의 통화를 라우팅합니다.

통화 경로를 정의할 때는 해당 경로와 연결된 트렁크를 지정하고, 경로와 연결된 중재 서버는 지정하지 않습니다. 대신 토폴로지 작성기를 사용하여 트렁크를 중재 서버와 연결합니다. 즉, 라우팅 시 통화에 사용할 트렁크가 결정되고 해당 트렁크와 연결된 중재 서버가 해당 통화에 대한 신호로 전송됩니다.

중재 서버는 풀로 배포할 수 있습니다. 이 풀은 프런트 엔드 풀과 함께 배치하거나 독립 실행형 풀로 배포할 수 있습니다. 중재 서버가 프런트 엔드 풀과 함께 배치될 경우 풀 크기가 12 미만이 될 수 있습니다(등록자 풀 크기 제한). 이러한 새 기능을 함께 사용하면 중재 서버에 대한 안정성과 배포 유연성이 향상되지만 다음 피어 엔터티에 관련 기능이 필요합니다.

  - **PSTN 게이트웨이.**Lync Server 2013 적격 게이트웨이는 적격 PSTN(공중 전화망) 게이트웨이가 중재 서버 풀의 부하 분산 장치 역할을 하여 풀 전체 통화의 부하를 분산시킬 수 있도록 DNS 부하 분산을 구현해야 합니다.

  - **세션 경계 컨트롤러.** SIP 트렁크의 경우 피어 엔터티는 인터넷 전화 통신 서비스 공급자의 SBC(세션 경계 컨트롤러)입니다. SBC는 중재 서버 풀에서 SBC의 방향으로 풀의 모든 중재 서버에서 오는 연결을 수신할 수 있습니다. 트래픽은 SBC에서 풀의 방향으로 풀의 모든 중재 서버에 전송될 수 있습니다. 이를 구현하는 한 가지 방법으로 서비스 공급자 및 SBC에서 지원하는 경우 DNS 부하 분산을 사용하는 방법이 있습니다. 대안으로 서비스 공급자에게 풀에 있는 모든 중재 서버의 IP 주소를 제공하고 서비스 공급자가 각 중재 서버에 대한 별도의 SIP 트렁크로 SBC에 이를 프로비전하는 방법이 있습니다. 그러면 서비스 공급자가 서버에 대한 부하 분산을 처리합니다. 모든 서비스 공급자 또는 SBC가 이러한 기능을 지원하는 것은 아닙니다. 또한 서비스 공급자가 이 기능에 대해 추가 요금을 부과할 수 있습니다. 일반적으로 SBC에 대한 각 SIP 트렁크에는 매월 요금이 부과됩니다.

  - **IP-PBX.** IP-PBX는 중재 서버 풀에서 IP-PBX SIP 종료의 방향으로 풀의 모든 중재 서버에서 오는 연결을 수신할 수 있습니다. 트래픽은 IP-PBX에서 풀의 방향으로 풀의 모든 중재 서버에 전송될 수 있습니다. 대부분의 IP-PBX는 DNS 부하 분산을 지원하지 않으므로 IP-PBX에서 풀의 각 중재 서버로의 개별 직접 SIP 연결을 정의하는 것이 좋습니다. 그러면 IP-PBX가 트렁크 그룹을 통해 트래픽을 분산시켜 부하 분산을 처리합니다. 이 경우 트렁크 그룹의 IP-PBX에 일관성 있는 라우팅 규칙 집합이 있다고 가정합니다. 특정 IP-PBX가 이 트렁크 그룹 개념을 지원하는지 여부에 관계 없이 중재 서버 클러스터가 IP-PBX와 올바르게 상호 작용하도록 할지 여부를 결정하기 전에 IP-PBX의 고유한 중복성 및 클러스터링 아키텍처와 상호 작용하는 방식을 결정해야 합니다.

중재 서버 풀에는 상호 작용하는 피어 게이트웨이에 대한 단일 보기가 있어야 합니다. 즉, 풀의 모든 구성원이 구성 저장소에서 피어 게이트웨이의 동일한 정의에 액세스하고 발신 전화에 대해 동일하게 상호 작용합니다. 따라서 일부 중재 서버가 발신 전화에 대해 특정 게이트웨이 피어와만 통신하도록 풀을 여러 조각으로 나눌 수 있는 방법이 없습니다. 이러한 조각화가 필요한 경우 별도의 중재 서버 풀을 사용해야 합니다. 예를 들어 이 항목에서 앞서 자세히 설명한 대로 풀과 상호 작용할 PSTN 게이트웨이, SIP 트렁크 또는 IP-PBX의 관련 기능이 없는 경우가 이에 해당합니다.

특정 PSTN 게이트웨이, IP-PBX 또는 SIP 트렁크 피어는 여러 중재 서버 또는 트렁크로 라우팅할 수 있습니다. 특정 중재 서버 풀이 제어할 수 있는 게이트웨이 수는 미디어 바이패스를 사용하는 통화 수에 따라 다릅니다. 신호 계층 처리만 필요하므로 다수의 통화가 미디어 바이패스를 사용하는 경우 풀의 중재 서버가 더 많은 통화를 처리할 수 있습니다.
