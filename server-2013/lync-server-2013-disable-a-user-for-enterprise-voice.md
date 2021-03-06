﻿---
title: Lync Server 2013에서 Enterprise Voice에 사용자 사용 안 함
TOCTitle: Lync Server 2013에서 Enterprise Voice에 사용자 사용 안 함
ms:assetid: 462002d8-21df-4d77-bf7f-4d059d6a4bb2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688043(v=OCS.15)
ms:contentKeyID: 49885745
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Enterprise Voice에 사용자 사용 안 함

 

_**마지막으로 수정된 항목:** 2012-09-21_

다음 절차에 따라 Lync Server 2013에 대해 설정된 사용자 계정의 Enterprise Voice를 해제합니다.

## Enterprise Voice에 대한 사용자 계정을 해제하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자**를 클릭합니다.

4.  **사용자 검색** 상자에 사용하도록 설정할 사용자 계정의 표시 이름, 이름, 성, SAM(보안 계정 관리자) 계정 이름, SIP 주소 또는 줄 URI(Uniform Resource Identifier)를 모두 또는 처음 부분을 입력하고 **찾기**를 클릭합니다.

5.  테이블에서 Enterprise Voice에 대해 설정하려는 사용자 계정을 클릭합니다.

6.  **편집** 메뉴에서 **세부 정보 표시**를 클릭합니다.

7.  **Lync Server 사용자 편집** 페이지의 **전화 통신** 아래에서 **Enterprise Voice**를 제외한 아무 옵션이나 클릭합니다.
    

    > [!NOTE]
    > 사용자가 Lync를 사용하여 오디오 또는 비디오 통화를 시작하지 못하도록 하려면 <STRONG>전화 통신</STRONG> 아래에서 <STRONG>오디오/비디오 사용 안 함</STRONG>을 클릭합니다.



8.  **커밋**을 클릭합니다.

사용자가 이제 Enterprise Voice 기능을 사용할 수 없습니다.

## 참고 항목

#### 작업

[Lync Server 2013에서 사용자가 Enterprise Voice를 사용할 수 있도록 설정](lync-server-2013-enable-users-for-enterprise-voice.md)  

#### 기타 리소스

[사용자에 대한 Enterprise Voice 관리](lync-server-2013-managing-enterprise-voice-for-users.md)  
[Lync Server 관리 셸](lync-server-2013-lync-server-management-shell.md)

