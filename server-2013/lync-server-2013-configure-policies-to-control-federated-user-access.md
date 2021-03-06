﻿---
title: 'Lync Server 2013: 페더레이션 사용자 액세스를 제어할 정책 구성'
TOCTitle: 페더레이션 사용자 액세스를 제어할 정책 구성
ms:assetid: 5485e208-81e4-4e59-9aeb-1232c11dd8a2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398359(v=OCS.15)
ms:contentKeyID: 49303655
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 페더레이션 사용자 액세스를 제어할 정책 구성

 

_**마지막으로 수정된 항목:** 2014-02-05_

페더레이션 파트너와의 통신을 지원할 정책을 구성할 경우 정책이 페더레이션 도메인의 사용자에 적용됩니다. 페더레이션 도메인 사용자가 Lync Server 2013 사용자와 공동 작업할 수 있는지 여부를 제어하기 위해 하나 이상의 외부 사용자 액세스 정책을 구성할 수 있습니다. 페더레이션 사용자 액세스를 제어하려면 전역, 사이트 및 사용자 수준에서 정책을 구성할 수 있습니다. 한 정책 수준에서 적용되는 Lync Server 정책 설정은 다른 정책 수준에서 적용되는 설정을 재정의할 수 있습니다. Lync Server 정책 우선 순위에 따르면 사용자 정책(최대 영향력)이 사이트 정책을 재정의한 후 사이트 정책이 글로벌 정책(최소 영향력)을 재정의합니다. 즉, 정책 설정이 해당 정책의 영향을 받는 개체에 가까울수록 개체에 미치는 영향력도 커집니다.


> [!NOTE]
> 조직에 대해 페더레이션을 사용하도록 설정하지 않았더라도 페더레이션 사용자 액세스를 제어하는 정책을 구성할 수 있습니다. 그러나 구성하는 정책은 조직에 대해 페더레이션을 사용하도록 설정하는 경우에만 유효합니다. 페더레이션을 사용하도록 설정하는 방법에 대한 자세한 내용은 배포 설명서 또는 작업 설명서에서 <A href="lync-server-2013-enable-or-disable-remote-user-access.md">Lync Server 2013에서 원격 사용자 액세스 사용 또는 사용 안 함</A>을 참고하세요. 또한 페더레이션 사용자 액세스를 제어하기 위한 사용자 정책을 지정하는 경우 해당 정책은 Lync Server 2013에 대해 사용하도록 설정되었으며 해당 정책을 사용하도록 구성된 사용자에게만 적용됩니다.



## 페더레이션 도메인 사용자의 액세스를 지원하기 위한 정책을 구성하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **외부 사용자 액세스** 를 클릭하고 **외부 액세스 정책** 을 클릭합니다.

4.  **외부 액세스 정책** 페이지에서 다음 중 하나를 수행합니다.
    
      - 페더레이션 사용자 액세스를 지원하기 위한 글로벌 정책을 구성하려면 글로벌 정책을 클릭하고 **편집** 을 클릭한 후에 **세부 정보 표시** 를 클릭합니다.
    
      - 새 사이트 정책을 만들려면 **새로 만들기** 를 클릭하고 **사이트 정책** 을 클릭합니다. **사이트 선택** 의 목록에서 적절한 사이트를 클릭하고 **확인** 을 클릭합니다.
    
      - 새 사용자 정책을 만들려면 **새로 만들기** 를 클릭하고 **사용자 정책** 을 클릭합니다. **새 외부 액세스 정책** 의 **이름** 필드에서 사용자 정책이 다루는 내용을 나타내는 고유한 이름을 만듭니다(예: 페더레이션 도메인 사용자에 대한 통신을 사용하도록 설정하는 사용자 정책의 경우 **EnableFederatedUsers** ).
    
      - 기존 정책을 변경하려면 테이블에 나열되어 있는 적절한 정책을 클릭하고 **편집** , **세부 정보 표시** 를 차례로 클릭합니다.

5.  (선택 사항) 설명을 추가하거나 편집하려면 정책에 대한 정보를 **설명** 에 지정합니다.

6.  다음 중 하나를 수행합니다.
    
      - 정책에 대한 페더레이션 사용자 액세스를 사용하도록 설정하려면 **페더레이션 사용자와의 통신 사용** 확인란을 선택합니다.
    
      - 정책에 대한 페더레이션 사용자 액세스를 사용하지 않도록 설정하려면 **페더레이션 사용자와의 통신 사용** 확인란 선택을 취소합니다.

7.  **커밋** 을 클릭합니다.

페더레이션 사용자 액세스를 허용하려면 조직에서 페더레이션을 지원하도록 설정해야 합니다. 자세한 내용은 [Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md)을 참조하십시오.

사용자 정책의 경우에는 페더레이션 사용자와 공동 작업하도록 할 사용자에게도 정책을 적용해야 합니다. 자세한 내용은 [Lync Server 2013에서 Lync 사용이 가능한 사용자에게 외부 사용자 액세스 정책 할당](lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md)을 참조하십시오.

## Windows PowerShell을 사용해서 페더레이션 도메인 사용자의 액세스를 지원하도록 기존 정책을 구성하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  Lync Server 관리 셸에 다음을 입력합니다.
    
        Set-CsExternalAccessPolicy -Identity <name of global, site or user policy - policy must exist when using Set-CsExternalAccessPolicy > -Description <descriptive name for policy> -EnableFederationAccess <$true, $false> -EnableXmppAccess <$true, $false> -EnablePublicCloudAcess <$true, $false> -EnablePublicCloudAudioVideoAcess <$true, $false> -EnableOutsideAcess <$true, $false>
    
    페더레이션 사용자 액세스, XMPP 도메인 액세스, 원격 사용자 액세스, 공용 공급자 액세스를 사용하도록 글로벌 정책을 설정하고 이를 지원하는 공용 공급자에 대해 오디오 및 비디오 사용 기능을 부여하는 예제 명령:
    
        Set-CsExternalAccessPolicy -Identity global -EnableFederationAccess $true -EnableXmppAccess $true -EnableOutsideAccess $true -EnablePublicCloudAccess $true -EnablePublicCloudAudioVideoAccess $true
    

    > [!TIP]
    > Lync Server 제어판 제어판에는 "EnablePublicCloudAudioVideoAccess" 매개 변수에 해당하는 선택 항목이 없습니다.



## Windows PowerShell을 사용해서 페더레이션 도메인 사용자의 액세스를 지원하도록 새 정책을 만들려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  Lync Server 관리 셸에 다음을 입력합니다.
    
        New-CsExtenalAccessPolicy -Identity <name of site or user policy - you cannot create a new global policy using New-CsExternalAccessPolicy > -Description <descriptive name for policy> -EnableFederationAccess <$true, $false> -EnableXmppAccess <$true, $false> -EnablePublicCloudAccess <$true, $false> -EnablePublicCloudAudioVideoAccess <$true, $false> -EnableOutsideAccess <$true, $false>
    
    새 사이트 정책을 만드는 예:
    
        New-CsExternalAccessPolicy -Identity site:Redmond -EnableFederationAccess $true -EnableXmppAccess $true -EnableOutsideAccess $true -EnablePublicCloudAccess $true -EnablePublicCloudAudioVideoAccess $true

## Windows PowerShell을 사용해서 페더레이션 도메인 사용자의 액세스를 지원하도록 정책을 삭제하거나 다시 설정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸에 다음을 입력합니다.
    
        Remove-CsExternalAccessPolicy -Identity <name of global, site or user policy> 
    
    글로벌 정책을 다시 설정하는 예(글로벌 정책은 해당 설정만 제거할 수 있으며, 정책 자체를 삭제할 수 없습니다.):
    
        Remove-CsExternalAccessPolicy -Identity global 
    
    사이트 정책을 제거하려면 다음을 입력합니다.
    
        Remove-CsExternalAccessPolicy -Identity site:Redmond 
    
    사이트 정책 Redmond를 삭제합니다. 이름이 UserEAPPolicy인 사용자 정책을 삭제하려면 다음을 입력합니다.
    
        Remove-CsExternalAccessPolicy -Identity UserEAPPolicy

## 참고 항목

#### 작업

[Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md)  
[Lync Server 2013에서 Lync 사용이 가능한 사용자에게 외부 사용자 액세스 정책 할당](lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md)  

#### 기타 리소스

[Lync Server 2013에서 조직의 SIP 페더레이션된 도메인 관리](lync-server-2013-manage-sip-federated-domains-for-your-organization.md)  
[Lync Server 2013에서 조직에 대한 SIP 페더레이션 공급자 관리](lync-server-2013-manage-sip-federated-providers-for-your-organization.md)  
[Set-CsExternalAccessPolicy](set-csexternalaccesspolicy.md)  
[New-CsExternalAccessPolicy](new-csexternalaccesspolicy.md)  
[Get-CsExternalAccessPolicy](get-csexternalaccesspolicy.md)  
[Remove-CsExternalAccessPolicy](remove-csexternalaccesspolicy.md)  
[Grant-CsExternalAccessPolicy](grant-csexternalaccesspolicy.md)

