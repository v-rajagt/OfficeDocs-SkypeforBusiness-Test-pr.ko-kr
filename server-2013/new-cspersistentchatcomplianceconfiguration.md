﻿---
title: New-CsPersistentChatComplianceConfiguration
TOCTitle: New-CsPersistentChatComplianceConfiguration
ms:assetid: a61b76a9-0e2b-4f64-b2fa-cddadc15451c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205163(v=OCS.15)
ms:contentKeyID: 49304619
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsPersistentChatComplianceConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

사이트 또는 서비스 범위에서 영구 채팅 준수 구성 설정의 새 컬렉션을 만듭니다. 관리자는 영구 채팅 준수를 통해 새 메시지, 새 이벤트(예: 사용자가 채팅방에 들어오거나 채팅방에서 나감), 파일 업로드/다운로드, 채팅 기록에 대해 실행된 검색 등 영구 채팅 항목 및 작업의 보관 파일을 유지 관리할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsPersistentChatComplianceConfiguration -Identity <XdsIdentity> [-AdapterName <String>] [-AdapterOutputDirectory <String>] [-AdapterType <String>] [-AddChatRoomDetails <$true | $false>] [-AddUserDetails <$true | $false>] [-Confirm [<SwitchParameter>]] [-CreateFileAttachmentsManifest <$true | $false>] [-CustomConfiguration <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-OneChatRoomPerOutputFile <$true | $false>] [-RunInterval <TimeSpan>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에 대해 영구 채팅 준수 구성 설정의 새 컬렉션을 만듭니다. 이 예제에서는 AddUserDetails 및 AddChatRoomDetails 속성이 모두 True($True)로 설정됩니다.

    New-CsPersistentChatComplianceConfiguration -Identity "site:Redmond" -AddUserDetails $True -AddChatRoomDetails $True

## 예제 2

예제 2에서도 Redmond 사이트에 대해 영구 채팅 준수 구성 설정의 새 컬렉션을 만드는 방법을 보여줍니다. 이 예제에서는 RunInterval 속성이 30분(00시간 : 30분 : 00초)으로 설정됩니다.

    New-CsPersistentChatComplianceConfiguration -Identity "site:Redmond" -RunInterval "00:30:00"

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

의료 및 금융 업계의 조직을 비롯한 대부분의 조직은 모든 전자 통신의 보관 파일을 유지 관리해야 합니다. 여기에는 영구 채팅 서비스를 사용하여 진행했을 수 있는 대화도 포함됩니다. Lync Server 2013에서는 영구 채팅방에서 대화한 모든 내용의 상세한 보관 파일을 유지하는 준수 데이터베이스를 별도로 만들 수 있습니다. 영구 채팅 준수는 사이트 범위 또는 서비스 범위에서 사용하거나 사용하지 않도록 설정할 수 있습니다. 즉, 지정된 영구 채팅 풀에 대해 준수를 사용하거나 사용하지 않도록 설정할 수 있습니다. 또한 영구 채팅 준수는 Windows PowerShell 명령줄 인터페이스를 통해서만 관리할 수 있으며 Lync Server 2013 제어판에서는 영구 채팅 준수 관리용 옵션을 사용할 수 없습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsPersistentChatComplianceConfiguration"}

Lync Server 제어판: **New-CsPersistentChatComplianceConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Xds ID</p></td>
<td><p>새로 만들 영구 채팅 준수 설정의 고유 식별자입니다. 새 준수 설정은 사이트 또는 서비스 범위(영구 채팅 서버 서비스에만 해당)에서 만들 수 있습니다. 사이트 범위에서 새 설정을 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>서비스 범위에서 새 설정을 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;service:PersistentChatServer:atl-gc-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>AdapterName</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>준수 설정에서 사용하는 영구 채팅 어댑터의 이름입니다. 어댑터는 준수 데이터베이스의 데이터를 특정 형식으로 변환하는 타사 제품입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AdapterOutputDirectory</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>어댑터 데이터가 저장되는 폴더의 전체 경로입니다. 각 어댑터에 대해 별도의 폴더를 지정해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AdapterType</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>Microsoft.Rtc.Internal.Chat.Server.Compliance.IComplianceAdapter 인터페이스를 구현하는 .NET 관리되는 유형의 정규화된 이름을 지정합니다. 이 어댑터는 타사에서 제공할 수도 있고, 내부 XML 어댑터인 &quot;Microsoft.Rtc.Internal.Chat.Server.Compliance.XmlAdapter,compliance&quot;로 설정할 수도 있습니다.</p>
<p>어댑터 유형을 지정하지 않으면 영구 채팅에서는 준수 데이터를 저장하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AddChatRoomDetails</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>True로 설정하면 각 채팅방에 대한 추가 세부 정보가 어댑터에 제공됩니다. 그러면 준수 데이터의 크기가 매우 커질 수 있습니다.</p>
<p>기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AddUserDetails</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>True로 설정하면 각 채팅방 사용자에 대한 추가 세부 정보가 어댑터에 제공됩니다. 그러면 준수 데이터의 크기가 매우 커질 수 있습니다.</p>
<p>기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CreateFileAttachmentsManifest</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>True로 설정하면 채팅방 내의 파일 전송을 추적하기 위해 추가 출력 파일을 만듭니다. 이러한 파일은 확장명이 .ATTACH이며, AdapterOutputDirectory에 의해 지정되는 위치에 저장됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CustomConfiguration</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>영구 채팅에서 준수 데이터를 사용자가 설계한 사용자 지정 형식으로 저장할 수 있도록 하는 XSLT 변환 스크립트입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OneChatRoomPerOutputFile</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>True로 설정하면 각 채팅방에 대해 별도의 보고서를 만듭니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RunInterval</em></p></td>
<td><p>선택</p></td>
<td><p>시간 범위</p></td>
<td><p>다음 출력 파일을 생성할 때까지 서버가 대기할 시간입니다. RunInterval은 일.시간:분:초 형식을 사용하여 지정해야 합니다. 예를 들어 RunInterval을 기본값인 30분으로 지정하려면 다음 구문을 사용합니다.</p>
<p>-RunInterval 00:30:00</p>
<p>RunInterval은 1분(00:01.00)에서 30일(30.00:00:00)(포함) 사이의 모든 값으로 설정할 수 있습니다. 기본값은 15분(00:15:00)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsPersistentChatComplianceConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsPersistentChatComplianceConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatComplianceConfiguration 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsPersistentChatComplianceConfiguration](get-cspersistentchatcomplianceconfiguration.md)  
[Remove-CsPersistentChatComplianceConfiguration](remove-cspersistentchatcomplianceconfiguration.md)  
[Set-CsPersistentChatComplianceConfiguration](set-cspersistentchatcomplianceconfiguration.md)

