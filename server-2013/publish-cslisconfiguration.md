﻿---
title: Publish-CsLisConfiguration
TOCTitle: Publish-CsLisConfiguration
ms:assetid: 54f9d653-075d-4533-b508-231f53b54db4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398364(v=OCS.15)
ms:contentKeyID: 49303667
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Publish-CsLisConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

LIS(위치 정보 서버) 구성을 중앙 관리 저장소에 게시합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Publish-CsLisConfiguration [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 명령은 LIS 구성을 중앙 관리 저장소에 적용합니다.

    Publish-CsLisConfiguration

## 자세한 정보

Lync Server에서 E9-1-1(Enhanced 9-1-1)을 구현하려면 와이어맵(wiremap)이라는 위치 매핑을 생성해야 합니다. 이 매핑에는 포트, 서브넷, 스위치 및 무선 액세스 지점과 일치하는 실제 주소가 포함되어 있으므로 Enterprise Voice 연결에 대해 수행된 호출이 가장 가까운 응급 운영자에게 도달하고 해당 운영자에게 올바른 발신자 위치를 제공합니다. **Set-CsLisPort** cmdlet 및 **Set-CsLisSubnet** cmdlet과 같은 cmdlet을 호출하여 만든 이 매핑 구성은 중앙 위치 데이터베이스에 저장됩니다. 이 cmdlet은 중앙 위치 데이터베이스의 변경 내용을 중앙 관리 저장소에 적용하여 위치 정보 서버에서 클라이언트에 위치를 렌더링할 수 있도록 정보를 위치 정보 서버에 복제합니다. **Unpublish-CsLisConfiguration** cmdlet을 호출하여 중앙 관리 저장소에서 구성을 제거할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Publish-CsLisConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Publish-CsLisConfiguration"}

## 매개 변수


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수</th>
<th>필수</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Debug-CsLisConfiguration](debug-cslisconfiguration.md)  
[Unpublish-CsLisConfiguration](unpublish-cslisconfiguration.md)  
[Import-CsLisConfiguration](import-cslisconfiguration.md)  
[Export-CsLisConfiguration](export-cslisconfiguration.md)  
[Test-CsLisConfiguration](test-cslisconfiguration.md)

