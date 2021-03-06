﻿---
title: 'Lync Server 2013: 오류 목록 보고서'
TOCTitle: 오류 목록 보고서
ms:assetid: b6f3a605-e0c6-461e-b17a-41d8039ace9d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg615446(v=OCS.15)
ms:contentKeyID: 49304805
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 오류 목록 보고서

 

_**마지막으로 수정된 항목:** 2015-03-09_

오류 목록 보고서에서는 실패한 피어 투 피어 또는 회의 세션에 참가한 개별 참가자에 대한 정보를 제공합니다. 이 정보에는 문제를 경험한 사용자의 URI와 실패와 관련된 SIP 응답 코드 및 진단 ID가 포함됩니다.

## 오류 목록 보고서 액세스

오류 목록 보고서는 [Lync Server 2013의 오류 분포 보고서](lync-server-2013-failure-distribution-report.md)에 있는 다음 메트릭 중 하나를 클릭하여 액세스됩니다.

  - 최상위 진단 이유(세션)

  - 최상위 형식(세션)

  - 최상위 풀(세션)

  - 최상위 원본(세션)

  - 최상위 구성 요소(세션)

  - 최상위 시작 사용자(세션)

  - 최상위 대상 사용자(세션)

  - 최상위 시작 사용자 에이전트(세션)

오류 목록 보고서에서는 피어 투 피어 세션에 대한 세션 세부 정보 메트릭을 클릭하여 [Lync Server 2013의 피어 투 피어 세션 정보 보고서](lync-server-2013-peer-to-peer-session-detail-report.md)에 액세스할 수 있습니다. 또한 전화 회의에 대한 전화 회의 메트릭을 클릭하여 전화 회의 정보 보고서에 액세스할 수 있습니다.

## 오류 목록 보고서의 효과적인 활용

오류 목록 보고서에서는 각 응답 코드 또는 각 진단 ID 위에 마우스를 놓기만 하면 해당 값에 대한 설명을 볼 수 있습니다. 예를 들어 진단 ID 7025 위에 마우스를 놓으면 도구 설명에 다음이 표시됩니다.

사용자를 위한 미디어를 만드는 동안 내부 서버 오류가 발생했습니다.

오류 목록 보고서는 하나 이상의 실패한 세션에 참가한 모든 사용자의 목록을 직접 검색하는 간편한 방법이나 실패한 세션에서 가장 자주 참여한 사용자를 파악하는 방법을 제공하지 않습니다. 우선 한 가지 이유는 오류 목록 보고서에 필터링 기능이 없기 때문입니다. 그러나 데이터를 내보낸 후에 쉼표로 구분된 값 파일로 변환할 경우 Windows PowerShell을 사용하여 이러한 사항을 찾을 수 있습니다. 예를 들어 데이터를 C:\\Data\\Failure\_List.csv라는 이름의 .CSV 파일로 저장한 경우 다음 명령을 사용하면 이 파일에 저장된 데이터를 기반으로 하나 이상의 실패한 세션에 참여한 모든 사용자가 나열됩니다.

    $failures = Import-Csv -Path " C:\Data\Failure_List.csv"
    $failure |Sort-Object "From user" | Select-Object "From user" -Unique

그러면 다음과 같은 목록이 반환됩니다.

    From user
    ----
    Pilar.Ackerman@litwareinc.com
    Henrik.Jensen@litwareinc.com
    Gilead.Amosnino@litwareinc.com
    David.Ahs@litwareinc.com
    Ken.Myer@litwareinc.com

다음 두 명령은 각 사용자가 참가한 실패한 총 세션 수를 보고합니다.

    $failures = Import-Csv -Path "C:\Data\Failure_List.csv"
    $failures | Group-Object "From user" | Select-Object Count, Name | Sort-Object -Property Count -Descending

그러면 다음과 같은 데이터가 반환됩니다.

    Count    Name
     -----    ----
        20    Pilar.Ackerman@litwareinc.com
        20    David.Ahs@litwareinc.com
        16    Gilead.Amosnino@litwareinc.com
        16    Ken.Myero@litwareinc.com
        14    Henrik.Jensen@litwareinc.com

## 필터

없음. 오류 목록 보고서는 필터링할 수 없습니다.

## 메트릭

다음 표에서는 각 실패한 통화에 대해 오류 목록 보고서에 제공된 정보를 보여 줍니다.

### 오류 목록 보고서 메트릭

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
<td><p><strong>보고된 시간</strong></p></td>
<td><p>아니요</p></td>
<td><p>보고서가 기록된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>요청</strong></p></td>
<td><p>아니요</p></td>
<td><p>실패한 SIP 요청 유형입니다. 예: INVITE 또는 BYE</p></td>
</tr>
<tr class="odd">
<td><p><strong>응답 코드</strong></p></td>
<td><p>아니요</p></td>
<td><p>회의가 실패했을 때 전송된 SIP 응답 코드입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>진단 ID</strong></p></td>
<td><p>아니요</p></td>
<td><p>오류 문제를 해결할 때 종종 유용한 정보를 제공하는 SIP 메시지에 연결된 고유 식별자(ms-diagnostics 헤더 형식)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>참가 소요 시간(밀리초)</strong></p></td>
<td><p>아니요</p></td>
<td><p>사용자가 전화 회의에 참가하기까지 소요된 시간(밀리초)입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>시작 사용자</strong></p></td>
<td><p>아니요</p></td>
<td><p>통화를 시작한 사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>출처 사용자 에이전트</strong></p></td>
<td><p>아니요</p></td>
<td><p>통화를 시작한 사용자의 끝점에 사용된 소프트웨어입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>대상 사용자</strong></p></td>
<td><p>아니요</p></td>
<td><p>통화를 받고 있는 사용자의 SIP 주소입니다.</p></td>
</tr>
</tbody>
</table>

