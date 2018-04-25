﻿---
title: ベスト プラクティス アナライザーの概要
TOCTitle: ベスト プラクティス アナライザーの概要
ms:assetid: c5fcaa05-eb1c-4092-90ad-177b127e795b
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg591349(v=OCS.15)
ms:contentKeyID: 48273541
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# ベスト プラクティス アナライザーの概要

 

_**トピックの最終更新日:** 2012-09-19_

Lync Server 2013、ベスト プラクティス アナライザーを使用して、Lync Server 2013 展開に関する問題を特定し、解決することができます。Lync Server 2013、ベスト プラクティス アナライザーは、Lync Server 2013 のコンポーネントから構成情報を収集します。

ベスト プラクティス アナライザーは、適切なネットワーク アクセスを使用することで、Active Directory ドメイン サービス、Exchange Server ユニファイド メッセージング (UM)、およびLync Server 2013 を実行するサーバーを調査できます。ベスト プラクティス アナライザーを使用して実行できるのは、以下の作業です。

  - 事前にチェックを実行して、推奨されるベスト プラクティスに従って構成が設定されていることを確認します。

  - Lync Server 2013 に必要な更新プログラムを自動的に検出します。

  - 最適化されていない構成設定、サポートされていないオプション、適用されていない更新プログラム、推奨されないプラクティスなど、問題の一覧を生成します。

  - 特定の問題のトラブルシューティングと修正を支援します。

ベスト プラクティス アナライザーは、以下の特徴を備えています。

  - 最小限のインストールの前提条件。

  - トラブルシューティングのヒントなど、レポートされた問題に関するオンライン ドキュメント。

  - 保存しておいて後で確認できる構成情報。

  - 最先端のシステム分析。

ベスト プラクティス アナライザーは、一組の XML 構成ファイルを使用して、Lync Server 2013 環境から収集する情報を決定します。Active Directory ドメイン サービスのチェックに加えて、Windows Management Instrumentation (WMI) での Windows Server オペレーティング システムのレジストリや設定などのソースをチェックします。

ベスト プラクティス アナライザーは、収集したデータを、Lync Server 2013 展開の設定と構成に関する事前定義されたルールのセットと比較します。

収集したデータと事前定義されたルールを比較した後で、このツールは問題をレポートします。レポートする問題ごとに、スキャンした Lync Server 2013 環境で検出された情報および推奨される構成に関する情報を提供します。また、特定の問題に関するさらに詳細な情報へのリンクも提供します。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Lync Server 2013、ベスト プラクティス アナライザーは、Lync Server 2013 のコンポーネントからのみ構成情報を収集します。以前の環境のスキャンには、このツールの以前のバージョンを使用することができます。詳細については、「<a href="lync-server-2013-requirements-for-running-best-practices-analyzer.md">ベスト プラクティス アナライザー実行の要件</a>」を参照してください。</td>
</tr>
</tbody>
</table>
