---
author: alkohli
ms.service: databox
ms.topic: include
ms.date: 09/25/2020
ms.author: alkohli
ms.openlocfilehash: 6dc201af2271909de15af9bac1a2e2bb68faed1a
ms.sourcegitcommit: 4313e0d13714559d67d51770b2b9b92e4b0cc629
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2020
ms.locfileid: "91400993"
---
Azure にデータを移動する際には、次の注意事項がデータに適用されます。

- 複数のデバイスが同じコンテナーに書き込まないようにすることをお勧めします。
- コピー対象のオブジェクトと同じ名前の既存の Azure オブジェクト (BLOB やファイルなど) がクラウド内にある場合、デバイスはクラウド内のファイルを上書きします。
- 共有フォルダーの下に作成される空のディレクトリ階層 (ファイルを含まない) は、BLOB コンテナーにアップロードされません。
- エクスプローラーでのドラッグ アンド ドロップまたはコマンド ラインを使用して、データをコピーできます。 コピーするファイルの合計サイズが 10 GB を超える場合は、Robocopy や rsync などの一括コピー プログラムを使用することをお勧めします。 一括コピー ツールは、断続的なエラーに対してコピー操作を再試行して、より高い回復性を提供します。
- Azure Storage コンテナーに関連付けられた共有から、作成時に共有に定義された BLOB の種類と一致しない BLOB がアップロードされた場合、そのような BLOB は更新されません。 たとえば、デバイス上にブロック BLOB の共有を作成します。 共有と、ページ BLOB がある既存のクラウド コンテナーを関連付けます。 その共有を更新してファイルをダウンロードします。 クラウドにページ BLOB として既に保存されている、更新されたファイルの一部を変更します。 アップロード エラーが表示されます。
- 共有にファイルを作成した後に、ファイル名を変更することはできません。
- 共有からファイルを削除しても、ストレージ アカウントのエントリは削除されません。
- データをコピーするために rsync を使用している場合、`rsync -a` オプションはサポートされません。

