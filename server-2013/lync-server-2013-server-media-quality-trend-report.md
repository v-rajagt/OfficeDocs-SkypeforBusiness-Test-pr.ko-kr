﻿---
title: Lync Server 2013의 서버 미디어 품질 추세 보고서
TOCTitle: Lync Server 2013의 서버 미디어 품질 추세 보고서
ms:assetid: 8a51fd13-1487-4632-b5ec-f7ae2abe8ed4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205071(v=OCS.15)
ms:contentKeyID: 49304304
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 서버 미디어 품질 추세 보고서

 

_**마지막으로 수정된 항목:** 2015-03-09_

서버 미디어 품질 추세 보고서는 통화량, 불량 통화율, 패킷 손실 및 지터와 같은 QoE(체감 품질) 메트릭으로 최대 5개 서버를 그래픽적으로 비교할 수 있는 방법을 제공합니다. 이를 통해 성능 품질이 낮은 서버, 활용률이 낮은 서버, 초과 사용되는 서버 등을 쉽게 식별할 수 있습니다.

## 서버 미디어 품질 추세 보고서 액세스

서버 미디어 품질 추세 보고서는 다음 보고서 중 하나에서 액세스할 수 있습니다.

  - [Lync Server 2013의 서버 성능 보고서](lync-server-2013-server-performance-report.md)(추세 메트릭 클릭)

  - [Lync Server 2013의 통화 정보 보고서](lync-server-2013-call-detail-report.md)(A/V 에지 서버 메트릭 클릭. 발신자 또는 수신자가 서버인 경우 끝점 이름을 클릭하여 서버 품질 미디어 추세 보고서에 연결할 수도 있습니다.)

## 서버 미디어 품질 추세 보고서 활용

특정 서버에 대한 [Lync Server 2013의 서버 성능 보고서](lync-server-2013-server-performance-report.md)에서 추세 메트릭을 클릭하면 서버 미디어 품질 추세 보고서가 열립니다. 하지만 해당 보고서가 공백으로만 표시되고 서버 성능 보고서에서 선택한 서버는 화면에 표시되지 않습니다. 대신 서버 드롭다운에서 해당 서버를 선택해야 합니다. 또한 서버 드롭다운에는 모두 선택 옵션이 있습니다. 서버가 5개 이상인 경우에는 이 옵션이 작동하지 않습니다. 서버 미디어 품질 추세 보고서는 한 번에 최대 5개의 서버에 대해서만 데이터를 표시할 수 있습니다.

서버 미디어 품질 추세 보고서로 표시되는 그래프에서 통화량, 불량 통화율로 표시된 점수는 핫링크입니다. 그래프에서 점수를 클릭하면 지정된 기간의 총 통화(또는 불량 통화)가 표시된 [Lync Server 2013의 통화 목록 보고서](lync-server-2013-call-list-report.md) 인스턴스가 열립니다.

## 필터

필터를 사용하면 여러 방식으로 반환된 데이터를 보거나 보다 세부적으로 대상화된 데이터 집합을 반환할 수 있습니다. 다음 표에서는 서버 미디어 품질 추세 보고서에 사용할 수 있는 필터 목록을 보여줍니다.

### 서버 미디어 품질 추세 보고서 필터

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
<p>7/7/2012 1:00 PM</p>
<p>시작 시간을 입력하지 않으면 보고서가 자동으로 지정된 날짜의 오전 12시부터 시작됩니다. 일별 데이터를 보려면 날짜만 입력합니다.</p>
<p>7/7/2012</p>
<p>주 또는 월별로 보려면 데이터를 보려는 해당 주 또는 월에 속하는 날짜를 입력합니다. 주 또는 월의 첫 번째 날짜를 입력할 필요가 없습니다.</p>
<p>7/3/2012</p>
<p>주는 항상 일요일부터 토요일까지로 실행됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>종료</strong></p></td>
<td><p>시간 범위의 종료 날짜/시간입니다. 시간별 데이터를 보려면 다음과 같이 종료 날짜 및 시간을 입력합니다.</p>
<p>7/7/2012 1:00 PM</p>
<p>종료 시간을 입력하지 않으면 보고서가 자동으로 지정된 날짜의 오전 12시에 종료됩니다. 일별 데이터를 보려면 날짜만 입력합니다.</p>
<p>7/7/2012</p>
<p>주 또는 월별로 보려면 데이터를 보려는 해당 주 또는 월에 속하는 날짜를 입력합니다. 주 또는 월의 첫 번째 날짜를 입력할 필요가 없습니다.</p>
<p>7/3/2012</p>
<p>주는 항상 일요일부터 토요일까지로 실행됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>간격</strong></p></td>
<td><p>시간 간격입니다. 다음 중 하나를 선택합니다.</p>
<ul>
<li><p>시간별(최대 25시간 표시 가능)</p></li>
<li><p>일별(최대 31일 표시 가능)</p></li>
<li><p>주별(최대 12주 표시 가능)</p></li>
</ul>
<p>시작 및 종료 날짜가 선택한 간격에 허용되는 최대 값 수를 초과하면 시작 날짜로부터 최대 값 수만 표시됩니다. 예를 들어 일별 간격을 선택하는 경우 시작 날짜가 2012/8/7이고 종료 날짜가 2012/9/28이면 2012/8/7 오전 12:00부터 2012/9/7 오전 12:00까지 총 31일의 데이터만 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>서버 유형</strong></p></td>
<td><p>통화에 포함된 서버 유형입니다. 허용되는 값은 다음과 같습니다.</p>
<ul>
<li><p>중재 서버</p></li>
<li><p>A/V 회의 서버</p></li>
<li><p>A/V 에지 서버</p></li>
<li><p>게이트웨이(중재 서버)</p></li>
<li><p>게이트웨이(중재 서버 바이패스)</p></li>
<li><p>AS 회의 서버</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>서버</strong></p></td>
<td><p>세션에 포함된 서버 이름입니다. 이 드롭다운 목록은 서버 유형 필터 값에 따라 자동으로 채워집니다. 보고서를 컴파일할 때는 최대 5개의 서버를 선택할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>액세스 유형</strong></p></td>
<td><p>참가자가 내부 네트워크 또는 외부 네트워크에 로그온되었는지 여부를 나타냅니다. 허용된 값은 다음과 같습니다.</p>
<ul>
<li><p>[모두]</p></li>
<li><p>내부</p></li>
<li><p>외부</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>네트워크 유형</strong></p></td>
<td><p>참가자가 연결된 네트워크 유형을 나타냅니다. 허용된 값은 다음과 같습니다.</p>
<ul>
<li><p>[모두]</p></li>
<li><p>유선</p></li>
<li><p>무선</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>VPN</strong></p></td>
<td><p>세션 중 외부 참가자가 VPN(가상 사설망) 연결을 사용 중이었는지를 나타냅니다. 허용된 값은 다음과 같습니다.</p>
<ul>
<li><p>[모두]</p></li>
<li><p>VPN</p></li>
<li><p>VPN 외</p></li>
</ul></td>
</tr>
</tbody>
</table>


## 메트릭

다음 표에서는 서버 미디어 품질 추세 보고서에 제공되는 정보를 보여 줍니다.

### 서버 미디어 품질 추세 보고서 메트릭

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
<td><p><strong>통화량</strong></p></td>
<td><p>아니요</p></td>
<td><p>총 통화 수입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>저하(MOS)</strong></p></td>
<td><p>아니요</p></td>
<td><p>통화 중 발생한 MOS(Mean Option Score) 저하의 평균 양입니다. 저하 값의 범위는 최저 0.0부터 최고 5.0까지 지정할 수 있습니다. 값이 0.5이하면 허용 가능한 저하 수준을 나타냅니다. 지금까지 평균 평가점은 사용자가 1부터 5까지 통화 품질의 등급을 지정하도록 하여 계산되었습니다. Lync Server은 모니터링 서버가 일련의 알고리즘을 사용하여 사용자가 통화에 대해 지정하는 등급을 예측합니다.</p>
<p>정체 현상, 대역폭 부족, 무선 통화 정체 또는 간섭, 미디어 서버 또는 끝점의 과부하 등의 경우에는 저하 값이 높게 나타날 수 있습니다. 저하 값이 높으면 오디오가 왜곡되거나 끊깁니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>불량 통화율</strong></p></td>
<td><p>아니요</p></td>
<td><p>불량으로 분류된 총 통화 수입니다. 불량 통화는 측정된 메트릭 중 적어도 하나 이상이 허용 값을 초과하는 모든 통화입니다(예: 지터가 과도하게 발생한 통화).</p></td>
</tr>
<tr class="even">
<td><p><strong>왕복(밀리초)</strong></p></td>
<td><p>아니요</p></td>
<td><p>RTP(실시간 전송 프로토콜) 패킷이 다른 끝점으로 이동한 후 다시 돌아오는 데 걸리는 평균 시간(밀리초)입니다. 적정 품질의 왕복 시간은 약 200밀리초 미만 정도로 간주됩니다.</p>
<p>국제 통화 라우팅, 잘못된 라우팅 구성 또는 미디어 서버 과부하 등으로 인해 왕복 값이 높게 발생할 수 있습니다. 왕복 시간이 높으면 양방향 실시간 오디오 대화가 어려워집니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>패킷 손실</strong></p></td>
<td><p>아니요</p></td>
<td><p>RTP(실시간 전송 프로토콜) 패킷 손실의 평균 비율입니다. (패킷 손실은 RTP 패킷, 인터넷을 통한 오디오 및 비디오 전송을 위해 사용되는 프로토콜인 RTP 패킷이 해당 목적지에 도달하지 못했을 때 발생합니다.) 정체 현상, 대역폭 부족, 무선 통화 정체 또는 간섭, 미디어 서버의 과부하 등의 경우에는 손실률이 높게 나타날 수 있습니다. 패킷 손실률이 높으면 오디오가 왜곡되거나 끊깁니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>지터(밀리초)</strong></p></td>
<td><p>아니요</p></td>
<td><p>RTP 패킷 도착 시간 사이에 발견된 평균 지터입니다. (지터는 통화 신호가 &quot;뒤섞인 정도&quot;를 나타냅니다.) 일반적으로 정체 현상, 미디어 서버 과부하 등의 경우에는 지터 값이 높게 발생하며 이로 인해 오디오가 왜곡되거나 끊깁니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>힐러 숨김 비율</strong></p></td>
<td><p>아니요</p></td>
<td><p>총 오디오 샘플 수에 대한 숨겨진 평균 오디오 샘플 비율입니다. (숨겨진 오디오 샘플은 손실된 네트워크 패킷으로 인해 발생하는 갑작스러운 전환을 매끄럽게 조정하기 위해 사용되는 기술입니다.) 값이 높으면 패킷 손실이나 지터로 인해 적용된 손실 숨김 수준이 높음을 의미하며 이로 인해 오디오가 왜곡되거나 끊깁니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>힐러 늘임 비율</strong></p></td>
<td><p>아니요</p></td>
<td><p>총 오디오 샘플 수에 대한 늘어진 평균 오디오 샘플 비율입니다. (늘어진 오디오는 손실된 네트워크 패킷이 감지되었을 때 통화 품질을 유지하기 위해 연장되는 오디오입니다.) 값이 높으면 지터로 인해 샘플 늘림 수준이 높음을 의미하며 이로 인해 오디오가 왜곡되거나 끊깁니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>힐러 압축 비율</strong></p></td>
<td><p>아니요</p></td>
<td><p>총 샘플 수에 대한 압축된 평균 오디오 샘플 비율입니다. (압축된 오디오는 손실된 네트워크 패킷이 감지되었을 때 통화 품질을 유지하기 위해 압축되는 오디오입니다.) 값이 높으면 지터로 인해 샘플 압축 수준이 높음을 의미하며 이로 인해 오디오가 빠르게 들리거나 왜곡됩니다.</p></td>
</tr>
</tbody>
</table>

