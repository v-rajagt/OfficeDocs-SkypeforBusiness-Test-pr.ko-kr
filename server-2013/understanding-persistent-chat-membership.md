﻿---
title: 영구 채팅 구성원 자격 이해
TOCTitle: 영구 채팅 구성원 자격 이해
ms:assetid: 900392d6-6e9f-4dae-93d6-39d7474409ef
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398730(v=OCS.15)
ms:contentKeyID: 49304371
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 영구 채팅 구성원 자격 이해

 

_**마지막으로 수정된 항목:** 2013-02-22_

영구 채팅방에 대한 사용자 액세스는 구성원 자격에 의해 관리됩니다. 메시지를 게시하고 읽을 수 있으려면 사용자가 채팅방의 구성원이어야 합니다. 채팅방에 대해 지정된 회원 정보를 갖고 있는 **발표자**만 **강당에 게시** 권한을 갖습니다. 강당은 발표자만 게시할 수 있고 다른 모든 사용자는 읽을 수만 있는 채팅방의 한 가지 유형(다른 채팅방은 **일반** 채팅방임)입니다.

또한 영구 채팅방은 특정 범주의 규칙에 따라 작동합니다. 범주에 대한 자세한 내용은 [Lync Server 2013에서 범주, 채팅방 및 추가 기능 관리](lync-server-2013-managing-categories-rooms-and-add-ins.md) 및 이 항목의 뒷 부분에 나오는 "범주 범위 지정 작동 방법" 및 "방 범주 전략" 항목을 참조하십시오.

영구 채팅 관리자는 채팅방 범주를 만들고 관리할 수 있습니다. 채팅방 범주를 만들고 관리할 때 영구 채팅 관리자는 특정 범주의 채팅방 구성원 또는 생성자가 될 수 있는 계정( Active Directory 도메인 서비스 그룹, 컨테이너 및 사용자)을 구성할 수 있습니다.

## Active Directory 도메인 서비스 및 영구 채팅

영구 채팅 서버는 내부 영구 채팅 사용자의 풀에 대해 Active Directory를 사용합니다. 영구 채팅(클라이언트)을 설치한 후 방 범주에 사용자 및 사용자 그룹의 도메인을 추가할 수 있습니다. 그런 다음 이러한 사용자 및 그룹을 방 범주의 구성원 자격에 추가할 수 있습니다.


> [!IMPORTANT]
> 영구 채팅방을 변경하려는 사용자의 이름이 중복되지 않았는지 확인해야 합니다. 사용자 이름이 중복되어 있으면 사용자가 항목을 변경할 때 차단되지 않도록 다른 이름으로 변경합니다. Active Directory에서 사용자 이름이 중복된 상태에서 사용자가 채팅방에서 항목을 변경하려고 하면 문제 해결을 위해 관리자에게 연락하라는 오류 메시지가 표시됩니다.



## 범주 범위 지정 작동 방식

범주는 **AllowedMembers** 속성에 따라 해당 범주에 있는 영구 채팅방의 구성원 자격 목록에서 구성원이 될 수 있는 모든 사용자 및 그룹을 지정합니다. 예를 들어 범주의 **AllowedMembers**를 contoso.com으로 설정하면 *Contoso* 에 있는 모든 그룹 또는 사용자를 해당 범주의 채팅방에 대한 구성원으로 추가할 수 있습니다. 범주에서 **AllowedMembers**를 *Sales* 로 설정하면 이 메일 그룹에 있는 그룹 및 사용자만 해당 범주의 채팅방에 대한 구성원으로 추가할 수 있습니다. 마찬가지로 **Creators** 속성을 사용하면 해당 범주에서 채팅방을 만들 수 있는 사용자를 제어할 수 있습니다. 채팅방을 만든 후에는 **AllowedMembers** 그룹의 누구라도 방에서 진행되는 관리 작업의 **관리자**로 지정할 수 있습니다(예: 구성원 자격 변경 및 승인).

범주에 대해 **AllowedMembers** 및 **Creators**를 정의하면 다음과 같은 이점이 있습니다.

  - 이 범주의 모든 채팅방에 범주 수준에서 설정된 제한 사항이 적용됩니다. 이를 통해 비즈니스 요구 및 액세스 정책을 기반으로 채팅방을 구분할 수 있습니다.

  - **Creators** 목록에 있는 사용자는 해당 범주에서 새 채팅방을 만들 수 있습니다. 조직에서 제한된 숫자의 사용자만 채팅방을 만들 수 있는 시스템을 구현하려는 경우 이 컨트롤을 사용해서 그러한 요구 사항을 충족시킬 수 있습니다.

## 방 범주 전략

범주의 **AllowedMembers**에는 이 범주의 모든 영구 채팅방을 사용하는 모든 사용자가 포함되어야 합니다. 비즈니스 데이터를 보고하고 적절한 액세스 수준을 보장하는 등 사용자의 요구 사항에 따라 방에서 검색 및 참가를 수행할 수 있는 사용자를 지정하기 위한 하나 이상의 범주를 정의해야 할 수 있습니다. 특정 사용자 집합(예: 중앙 지원 데스크 또는 정식 직원)만 방을 만들 수 있도록 허용하려면 해당 요구 사항을 충족하는 범주의 **Creators** 범위를 지정할 수 있습니다.

또한 범주를 사용해서 교신 차단 영역을 만들 수 있습니다. 교신 차단 영역은 조직 내 이해 관계가 충돌하지 않도록 방지합니다. 예를 들어 특정 관리자가 거래자 범주로만 채팅방을 만들고 다른 범주의 채팅방은 분석가만 사용할 수 있습니다.


> [!NOTE]
> Lync Server 2013, 영구 채팅 서버에서는 페더레이션 사용자에 대한 액세스를 지원하지 않습니다. 이전 버전의 영구 채팅 서버에서 페더레이션 사용자의 채팅이 있으면 마이그레이션이 수행됩니다. 페더레이션된 사용자는 사용하지 않도록 설정된 계정으로 추가됩니다.



## 구성원을 사용자 그룹으로 제한

범주에 도메인을 추가하면 해당 도메인에 포함되는 그룹 개체의 사용자 그룹을 사용하여 이러한 사용자 그룹을 해당 범주의 방 구성원으로 지정할 수 있습니다.

일반적으로는 범주의 **AllowedMembers** 및 **Creators**를 정의할 때 Active Directory 컨테이너(예: 도메인 및 조직 단위)를 사용하는 것이 좋습니다. 모든 도메인의 개체를 **AllowedMembers** 또는 **Creators** 목록에 추가할 수 있습니다. **AllowedMembers** 또는 **Creators** 목록 내의 개체만 해당 범주 아래의 방에 추가할 수 있습니다.

