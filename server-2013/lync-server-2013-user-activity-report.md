﻿---
title: 'Lync Server 2013: 사용자 활동 보고서'
TOCTitle: 사용자 활동 보고서
ms:assetid: 3aa6fef2-ea02-4f0f-93e8-fa2e0a953d79
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558638(v=OCS.15)
ms:contentKeyID: 49303354
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 사용자 활동 보고서

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자 활동 보고서에서는 지정된 기간 동안 사용자가 수행한 피어 투 피어 및 회의 세션의 자세한 목록을 제공합니다. 대부분의 모니터링 보고서와 달리 사용자 활동 보고서에서는 각 전화가 개별 사용자와 연결됩니다. 예를 들어 피어 투 피어 세션은 전화를 시작한 사람(보낸 사용자)과 해당 전화를 거는 대상(대상 사용자)의 SIP URI를 지정합니다. 전화 회의에 대해 정보를 확장하면 모든 전화 회의 참가자 및 참가자들이 해당 전화 회의에 대해 보유한 역할의 목록이 표시됩니다.

사용자 활동 보고서는 "지원 센터" 보고서라고도 합니다. 이 보고서는 지원 센터 담당자가 특정 사용자에 대한 세션 정보를 검색하는 데 사용하는 경우가 많기 때문입니다. 사용자 URI 접두사 상자에 사용자의 SIP URI만 입력하면 개별 사용자가 걸거나 받은 전화를 필터링할 수 있습니다.

예를 들어 URI 상자에 **ken** 을 입력하면 사용자 활동 보고서에서는 **Ken** .Myer@litwareinc.com을 찾지만 다음 사용자도 함께 찾습니다.

  - **ken**azi@litwareinc.com

  - **ken**burg@litwareinc.com

  - **Ken** .Sanchez@litwareinc.com

  - **Ken** nedy@litwareinc.com

Ken Myer에 해당하는 정보만 반환하려면 검색 상자에 전체 URI(Ken.Myer@litwareinc.com)를 입력하거나 조직의 다른 사용자로부터 고유하게 식별할 수 있는 Ken의 충분한 URI 정보를 입력합니다.

Ken.my

## 사용자 활동 보고서에 액세스하려면

사용자 활동 보고서는 모니터링 보고서 홈 페이지에서 액세스합니다. [Lync Server 2013의 IP 전화 인벤토리 보고서](lync-server-2013-ip-phone-inventory-report.md)에서 사용자 URI 메트릭을 클릭하여 사용자 활동 보고서에 액세스할 수도 있습니다. 사용자 활동 보고서 내에서 전화 회의에 대해 전화 회의 URI를 클릭하면 전화 회의 정보 보고서로 이동합니다. 마찬가지로, 피어 투 피어 통화에 대해 정보 메트릭을 클릭하면 [Lync Server 2013의 피어 투 피어 세션 정보 보고서](lync-server-2013-peer-to-peer-session-detail-report.md)로 이동합니다.

## 사용자 활동 보고서를 가장 효율적으로 활용

사용자 활동 보고서에는 유용한 정보가 많지만 이러한 정보를 찾기가 어려운 경우도 있습니다. 예를 들어 지정된 기간 동안 조직에서 수행되는 모든 사용자 활동이 사용자 활동 보고서에 포함되기 때문에, 실제로 특정 방식으로 Microsoft Lync Server 2013을 사용한 사용자에 대한 정보는 찾기가 어려울 수 있습니다.


> [!WARNING]
> 기술적으로는 일부 사용자 활동이 기록되지 않을 수 있습니다. Lync Server에서는 모든 전화 통화에 대한 정보를 유지하려고 하지만, 특정 통화에 대한 정보가 데이터베이스에 기록되지 않을 수도 있습니다. Lync Server는 Lync Server 2013 사용 방식에 대한 매우 정확한 정보를 제공하도록 디자인되어 있기는 하지만 이 정보가 완벽한 것은 아닙니다. 이처럼 모든 통화가 기록된다는 보장이 없기 때문에 Lync Server 모니터링을 결제 시스템으로 사용해서는 안 됩니다.<BR>둘째로, 모니터링 보고서에서는 레코드를 1,000개까지만 표시할 수 있습니다. 따라서 사용자 활동의 양과 작업 기간에 따라서는 쿼리가 데이터베이스에 실제로 저장되어 있는 모든 데이터를 반환하지는 않을 수도 있습니다.



  - 해당 기간 동안 실제로 시스템을 사용한 사용자

  - 해당 기간 동안 가장 많은 활동을 한 사용자

  - 전화 통화를 가장 많이 한 사용자 및 가장 많은 인스턴트 메시징 세션에 참가한 사용자

이러한 정보를 확인하려면 모니터링 보고서에서 검색된 데이터를 Excel 스프레드시트로 내보내면 됩니다. 그런 다음 해당 스프레드시트 및/또는 쉼표로 구분된 값 파일을 사용하여 사용자 활동 보고서에서 가능한 방식으로 데이터를 분석합니다. 예를 들어 보고서 데이터를 Excel로 내보낸 다음 쉼표로 구분된 값 파일로 내보냈다고 가정하겠습니다. 이 경우 다음과 같은 명령을 사용하면 .CSV 파일의 데이터를 Windows PowerShell로 가져올 수 있습니다.

    $x = Import-Csv -Path "C:\Data\User_Activity_Report.csv"

데이터를 가져온 후에는 간단한 Windows PowerShell 명령을 사용하여 원하는 정보를 확인할 수 있습니다. 예를 들어 다음 명령은 하나 이상의 세션에서 "시작 사용자" 역할을 한 고유 사용자의 목록을 반환합니다.

    $x | Group-Object "From user" | Select Name | Sort-Object Name

즉, 다음과 같은 결과가 반환됩니다.

    Name
    ----
    David.Ahs@litwareinc.com
    Gilead.Amosnino@litwareinc.com
    Henrik.Jensen@litwareinc.com
    Ken.Myer@litwareinc.com
    Pilar.Ackerman@litwareinc.com

다음 명령은 사용자가 참가한 총 세션 수를 기준으로 고유 사용자 목록을 표시합니다.

    $x | Group-Object "From user" | Select Count, Name | Sort-Object Count -Descending

이 명령을 실행하면 다음과 같은 데이터가 반환됩니다.

    Count    Name
    -----    ----
      523    Ken.Myer@litwareinc.com
       63    David.Ahs@litwareinc.com
       29    Pilar.Ackerman@litwareinc.com
       17    Gilead.Amosnino@litwareinc.com
       10    Henrik.Jensen@litwareinc.com

다음 명령은 형식으로 오디오를 포함한 세션만 보고합니다.

    $x | Where-Object {$_.Modalities -match "audio"} | Group-Object "From user" | Select Count, Name | Sort-Object Count -Descending

보고서에 표시되는 진단 ID 위에 마우스를 놓으면 해당 ID에 대해 설명하는 도구 설명이 나타납니다.

## 필터

필터를 사용하면 여러 방식으로 반환된 데이터를 보거나 보다 세부적으로 대상화된 데이터 집합을 반환할 수 있습니다. 예를 들어 사용자 활동 보고서에서는 활동 유형과 같은 항목(즉, 피어 투 피어 세션 또는 회의 세션) 또는 사용자의 SIP 주소(한 사용자의 활동 보기 허용)에 따라 반환된 데이터를 필터링할 수 있습니다. 또한 데이터의 그룹 지정 방식도 선택할 수 있습니다. 이 경우 사용은 시간, 일, 주 및 월별로 그룹이 지정됩니다.

다음 표에서는 사용자 활동 보고서에서 사용할 수 있는 필터를 보여 줍니다.

### 사용자 활동 보고서 필터

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>이름</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>시작</strong></p></td>
<td><p>시간 범위의 시작 날짜/시간입니다. 시간별 데이터를 보려면 다음과 같이 시작 날짜 및 시간을 입력합니다.</p>
<p>7/17/2012 1:00 PM</p>
<p>시작 시간을 입력하지 않으면 보고서가 자동으로 지정된 날짜의 오전 12시부터 시작됩니다. 일별 데이터를 보려면 날짜만 입력합니다.</p>
<p>7/17/2012</p>
<p>주 또는 월별로 보려면 데이터를 보려는 해당 주 또는 월에 속하는 날짜를 입력합니다. 주 또는 월의 첫 번째 날짜를 입력할 필요가 없습니다.</p>
<p>7/13/2012</p>
<p>주는 항상 일요일부터 토요일까지로 실행됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>종료</strong></p></td>
<td><p>시간 범위의 종료 날짜/시간입니다. 시간별 데이터를 보려면 다음과 같이 종료 날짜 및 시간을 입력합니다.</p>
<p>7/17/2012 1:00 PM</p>
<p>종료 시간을 입력하지 않으면 보고서가 자동으로 지정된 날짜의 오전 12시에 종료됩니다. 일별 데이터를 보려면 날짜만 입력합니다.</p>
<p>7/17/2012</p>
<p>주 또는 월별로 보려면 데이터를 보려는 해당 주 또는 월에 속하는 날짜를 입력합니다. 주 또는 월의 첫 번째 날짜를 입력할 필요가 없습니다.</p>
<p>7/13/2012</p>
<p>주는 항상 일요일부터 토요일까지로 실행됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>활동 유형</strong></p></td>
<td><p>활동 유형입니다. 다음 중 하나를 선택합니다.</p>
<ul>
<li><p>[모두]</p></li>
<li><p>피어 투 피어</p></li>
<li><p>전화 회의</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>형식</strong></p></td>
<td><p>사용 가능한 형식은 선택한 활동 유형에 따라 다릅니다. 활동 유형이 피어 투 피어인 경우 형식에 따라 메신저, 파일 전송, 응용 프로그램 공유, 음성 또는 비디오를 선택할 수 있습니다.</p>
<p>활동 유형이 회의인 경우에는 메신저 전화 회의, 웹 회의, 응용 프로그램 공유, 음성/비디오 회의 또는 전화 통신 회의를 선택할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>세션 범주</strong></p></td>
<td><p>문제가 있는 활동이 성공 또는 실패했는지를 나타냅니다. 다음 중 하나를 선택합니다.</p>
<ul>
<li><p>[모두]</p></li>
<li><p>성공</p></li>
<li><p>예상 오류</p></li>
<li><p>예기치 않은 오류</p></li>
</ul>
<p>&quot;예상 오류&quot;는 발생할 것으로 예상된 오류입니다. 예를 들어 사용자가 자신의 상태를 방해 금지로 설정한 경우 해당 사용자에 대한 통화가 실패할 것으로 예상할 수 있습니다. &quot;예기치 않은 오류&quot;는 일반적으로 정상 상태의 시스템으로 보이지만 예기치 않게 발생한 오류입니다. 예를 들어 발신자가 보류 상태일 때는 통화가 종료되지 않아야 합니다. 하지만 통화가 종료되면 바로 예기치 않은 오류로 플래그 지정됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>사용자 URI 접두사</strong></p></td>
<td><p>사용자의 SIP 주소입니다. 사용자 Ken Myer에 대한 레코드만 보려면 Ken Myer의 SIP 주소를 입력해야 합니다. 예:</p>
<p>sip:kenmyer@litwareinc.com</p></td>
</tr>
</tbody>
</table>


## 피어 투 피어 세션에 대한 메트릭

다음 표에서는 피어 투 피어 세션(즉, 참가자가 두 명뿐인 세션)에 대해 사용자 활동 보고서에 제공되는 정보를 보여 줍니다.

### 피어 투 피어 세션에 대한 메트릭

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>이름</th>
<th>이 항목에 대한 정렬 가능 여부</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>세부 정보</strong></p></td>
<td><p>아니요</p></td>
<td><p>이 항목을 클릭하면 보고서에 선택한 세션에 대한 피어 투 피어 세션 세부 정보 보고서가 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>시작 사용자</strong></p></td>
<td><p>예</p></td>
<td><p>피어 투 피어 세션을 시작한 사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>대상 사용자</strong></p></td>
<td><p>예</p></td>
<td><p>피어 투 피어 세션에 참가한 사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>형식</strong></p></td>
<td><p>예</p></td>
<td><p>세션에 사용된 통신 유형입니다. 예: IM, 오디오 또는 파일 전송.</p></td>
</tr>
<tr class="odd">
<td><p><strong>초대 시간</strong></p></td>
<td><p>예</p></td>
<td><p>피어 투 피어 세션에 참가하라는 최초 초대가 전송된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>응답 시간</strong></p></td>
<td><p>예</p></td>
<td><p>&quot;대상&quot; 사용자가 세션 초대를 수락한 날짜 및 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>종료 시간</strong></p></td>
<td><p>예</p></td>
<td><p>피어 투 피어 세션이 종료된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>진단 ID</strong></p></td>
<td><p>예</p></td>
<td><p>오류 문제를 해결할 때 종종 유용한 정보를 제공하는 SIP 메시지에 연결된 고유 식별자(ms-diagnostics 헤더 형식)입니다. 진단 헤더는 선택 사항이며(이러한 헤더를 포함하지 않는 SIP 세션도 가능함) 진단 ID는 일부 유형의 문제가 발생한 세션에 대해서만 보고됩니다.</p></td>
</tr>
</tbody>
</table>


## 회의 세션에 대한 메트릭

다음 표에서는 회의 세션(즉, 참가자가 세 명 이상인 세션)에 대해 사용자 활동 보고서에 제공되는 정보를 보여 줍니다.

### 회의 세션에 대한 메트릭

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>이름</th>
<th>이 항목에 대한 정렬 가능 여부</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>전화 회의 URI</strong></p></td>
<td><p>예</p></td>
<td><p>고유한 회의 식별자입니다. 이 항목을 클릭하면 보고서에 선택한 세션에 대한 회의 세부 정보 보고서가 표시됩니다. 이 항목을 확장하면 보고서에 회의 참가자에 대한 정보가 표시됩니다. 자세한 내용은 이 항목의 뒷부분에 나오는 &quot;회의 참가자에 대한 메트릭&quot; 섹션을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>이끌이</strong></p></td>
<td><p>예</p></td>
<td><p>회의를 구성한 사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>풀</strong></p></td>
<td><p>예</p></td>
<td><p>회의에 사용된 에지 서버(있는 경우)의 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>시작 시간</strong></p></td>
<td><p>예</p></td>
<td><p>회의가 시작된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>종료 시간</strong></p></td>
<td><p>예</p></td>
<td><p>회의가 종료된 날짜 및 시간입니다.</p></td>
</tr>
</tbody>
</table>


## 회의 참가자에 대한 메트릭

다음 표에서는 회의의 각 참가자에 대해 제공되는 사용자 활동 보고서에 제공된 정보를 보여 줍니다.

### 회의 참가자에 대한 메트릭

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>이름</th>
<th>이 항목에 대한 정렬 가능 여부</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>역할</strong></p></td>
<td><p>아니요</p></td>
<td><p>사용자에 대한 회의 역할(예: 발표자)입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>참가자</strong></p></td>
<td><p>아니요</p></td>
<td><p>사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>연결</strong></p></td>
<td><p>아니요</p></td>
<td><p>네트워크 연결 유형입니다. 예를 들어 내부 연결의 경우에는 &quot;내부 발신&quot;이고 전화 접속 사용자의 경우에는 &quot;보낸 PSTN&quot;입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>참가 시간</strong></p></td>
<td><p>아니요</p></td>
<td><p>사용자가 회의에 참가한 날짜 및 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>나간 시간</strong></p></td>
<td><p>아니요</p></td>
<td><p>사용자가 회의에서 나간 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>진단 ID</strong></p></td>
<td><p>아니요</p></td>
<td><p>오류 문제를 해결할 때 종종 유용한 정보를 제공하는 SIP 메시지에 연결된 고유 식별자(ms-diagnostics 헤더 형식)입니다. 진단 헤더는 선택 사항이며(이러한 헤더를 포함하지 않는 SIP 세션도 가능함) 진단 ID는 일부 유형의 문제가 발생한 세션에 대해서만 보고됩니다.</p></td>
</tr>
</tbody>
</table>
