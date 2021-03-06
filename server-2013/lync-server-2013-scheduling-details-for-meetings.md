﻿---
title: スケジューリングの詳細
TOCTitle: スケジューリングの詳細
ms:assetid: 39ca6fff-2c15-4347-9f1f-6c8687a39a49
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ204823(v=OCS.15)
ms:contentKeyID: 48271797
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# スケジューリングの詳細

 

_**トピックの最終更新日:** 2012-10-04_

要求された時間に、その他の会議がスケジュール設定されていないことを確認した後で、要求を処理する大規模会議サポートスタッフは、大規模会議プールに会議をスケジュール設定します。Lync Server 2013 クライアントと共にインストールされた Lync 用オンライン ミーティング アドインを使用してこの作業を行います。この時、専用の大規模会議プールで Lync Server に対して有効なユーザーの資格情報を使用します。

最良のユーザー エクスペリエンスを保証するには、会議の開催者の需要を満たす適切なアクセスレベルと会議設定で、大規模会議をスケジュール設定することが重要です。Lync 会議オプションでは、以下のスケジュール設定を構成することを推奨します。

  - 専用の会議スペースを再利用せずに、各大規模会議用に新しい会議スペースを使用します。

  - 以下のように会議アクセス レベルを指定します。
    
      - 1 名でも組織外部の招待者がいる場合は、会議アクセスの種類を \[**すべてのユーザー (制限なし)**\] に設定します。これにより、会議の進行中に、大規模なロビーを管理することを回避できます。
    
      - 会議が内部のみの会議の場合、会議アクセスの種類を \[**同じ組織のユーザー**\] に設定します。
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>会議アクセスの種類を [<strong>会社内から招待した人</strong>] に設定することは避けてください。この設定を使用すると、開催者は招待者リストにすべてのユーザーの電子メール アドレスを追加する必要があり、また配布グループを招待できません。<br />
        会議アクセスの種類を、[<strong>会議の開催者である自分のみ</strong>] に設定することは避けてください。この設定では、発表者を含む会議の参加者全員を、会議実行時にロビーに配置する必要があるからです。この場合、大規模会議の実行責任者は、継続的にロビー名簿を監視して、ロビーにいる新規ユーザーの参加を許可する必要があります。</td>
        </tr>
        </tbody>
        </table>


  - \[**発信者は直接参加する**\] 設定のチェックボックスをオンにして、電話からダイヤルインするユーザーが、自動的に会議に参加できるようにします。

  - 以下のユーザーは明示的に招待します。
    
      - 会議の主催者と代理人 (要求者)
    
      - 会議の要求者が提出した発表者のリスト
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>会議アクセスの種類が [<strong>選択した個人</strong>] に設定された場合、大規模会議の各参加者を、会議の招待者として明示的に追加する必要があります。</td>
    </tr>
    </tbody>
    </table>


  - 発表者は明示的に管理してください。発表者オプションをいずれかの自動昇格値に設定しないでください。以下のユーザーは必ず発表者として追加します。
    
      - 会議の主催者と代理人 (要求者)
    
      - 大規模会議の要求者が提出した発表者のリスト
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>発表者を明示的に管理することによって、発表者の数を制御できます。これにより、発表者を少数に制限して、効果的な大規模会議ができます。会議の参加者の大部分が参加者役割を持っていれば、誤ってプレゼンテーションの制御を取得する、PowerPoint プレゼンテーションを削除する、発表者のミュートを切り替えるなど、また、その他の会議の中断をもたらす可能性を減らすのに役立ちます。</td>
    </tr>
    </tbody>
    </table>


  - 発表者だけが会議に音声をブロードキャストできるように、\[**すべての参加者をミュートにする**\] 設定のチェック ボックスをオンにします。

  - 発表者だけが会議にビデオをブロードキャストできるように、\[**出席者のビデオをブロックする**\] 設定のチェック ボックスをオンにします。

以下の図は Lync 用オンライン ミーティング アドインの推奨設定を示します。

![会議のオプション](images/JJ204823.54e4e70d-06b0-45cd-8d94-bab649cd5dc0(OCS.15).jpg "会議のオプション")

