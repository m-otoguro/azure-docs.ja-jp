---
title: QnA Maker サービスを設定する - QnA Maker
description: QnA Maker のナレッジ ベースを作成する前に、まず Azure で QnA Maker サービスをセットアップしておく必要があります。 QnA Maker サービスは、サブスクリプション内で新しいリソースを作成することが認可されているユーザーであれば、だれでもセットアップできます。
ms.service: cognitive-services
ms.subservice: qna-maker
ms.topic: conceptual
ms.date: 11/09/2020
ms.openlocfilehash: beb45d0d650b07f6106a3307d2d3a955095ee8b1
ms.sourcegitcommit: f377ba5ebd431e8c3579445ff588da664b00b36b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99592264"
---
# <a name="manage-qna-maker-resources"></a>QnA Maker のリソースを管理する

QnA Maker のナレッジ ベースを作成する前に、まず Azure で QnA Maker サービスをセットアップしておく必要があります。 QnA Maker サービスは、サブスクリプション内で新しいリソースを作成することが認可されているユーザーであれば、だれでもセットアップできます。

リソースを作成する前に、次の概念について十分に理解しておくことをお勧めします。

* "[QnA Maker のリソース](../Concepts/azure-resources.md)"
* [キーの作成と発行](../Concepts/azure-resources.md#keys-in-qna-maker)

## <a name="create-a-new-qna-maker-service"></a>新しい QnA Maker サービスの作成

# <a name="qna-maker-ga-stable-release"></a>[QnA Maker GA (安定版リリース)](#tab/v1)

この手順では、ナレッジ ベースのコンテンツを管理するために必要な Azure リソースを作成します。 これらの手順を完了すると、Azure portal のリソース用の **[キー]** ページに、_サブスクリプション_ キーが表示されます。

1. Azure portal にサインインし、[QnA Maker リソースを作成](https://ms.portal.azure.com/#create/Microsoft.CognitiveServicesQnAMaker)します。

1. 使用条件を読んだ後、 **[作成]** を選択します。

    ![新しい QnA Maker サービスの作成](../media/qnamaker-how-to-setup-service/create-new-resource-button.png)

1. **QnA Maker** で、適切なレベルとリージョンを選択します。

    ![新しい QnA Maker サービスを作成する - 価格レベルとリージョン](../media/qnamaker-how-to-setup-service/enter-qnamaker-info.png)

    * **[名前]** フィールドに、この QnA Maker サービスを識別する一意の名前を入力します。 ナレッジ ベースが関連付けられる QnA Maker のエンドポイントも、この名前によって識別されます。
    * QnA Maker リソースのデプロイ先となる **サブスクリプション** を選択します。
    * QnA Maker 管理サービス (ポータルおよび Management API) の **価格レベル** を選択します。 [詳細については、SKU の価格](https://aka.ms/qnamaker-pricing)に関するページをご覧ください。
    * この QnA Maker リソースのデプロイ先として、新しい **リソース グループ** を作成する (推奨) か、既存のリソース グループを使用します。 QnA Maker はいくつかの Azure リソースを作成します。 これらのリソースを保持するリソース グループを作成すると、リソースの検索、管理、および削除を、リソース グループ名によって簡単に実行できます。
    * **リソース グループの場所** を選択します。
    * Azure Cognitive Search サービスの **検索価格レベル** を選択します。 Free レベル オプションを利用できない (灰色表示されている) 場合、それは、ご利用のサブスクリプションで Free サービスが既にデプロイされていることを意味します。 その場合は、Basic レベルから開始する必要があります。 [Azure Cognitive Search の価格の詳細](https://azure.microsoft.com/pricing/details/search/)に関するページを参照してください。
    * Azure Cognitive Search インデックスのデプロイ先となる **検索場所** を選択します。 顧客データをどの場所に格納する必要があるかの制限に基づいて、Azure Cognitive Search で使用する場所を選択できます。
    * **[アプリ名]** フィールドに、Azure App Service インスタンスの名前を入力します。
    * App Service の既定のレベルは Standard (S1) になります。 このプランは、作成後に変更することができます。 詳細については、「[App Service の価格](https://azure.microsoft.com/pricing/details/app-service/)」をご覧ください。
    * App Service のデプロイ先となる **Web サイトの場所** を選択します。

        > [!NOTE]
        > **検索場所** は **Web サイトの場所** と異なっていてもかまいません。

    * **Application Insights** を有効にするかどうかを選択します。 **Application Insights** を有効にした場合、トラフィック、チャットのログ、エラーに関するテレメトリが QnA Maker によって収集されます。
    * Application Insights リソースのデプロイ先となる **App Insights の場所** を選択します。
    * コスト削減対策として、QnA Maker 用に作成する Azure リソースのすべてではなく、一部を[共有](#configure-qna-maker-to-use-different-cognitive-search-resource)することができます。

1. すべてのフィールドを確認した後、 **[作成]** を選択します。 プロセスが完了するまでに数分かかることがあります。

1. デプロイが完了すると、サブスクリプション内に次のリソースが作成されていることがわかります。

   ![リソースによって新しい QnA Maker サービスが作成された](../media/qnamaker-how-to-setup-service/resources-created.png)

    種類が _Cognitive Services_ であるリソースには、_サブスクリプション_ キーがあります。

# <a name="qna-maker-managed-preview-release"></a>[QnA Maker マネージド (プレビュー リリース)](#tab/v2)

この手順では、ナレッジ ベースのコンテンツを管理するために必要な Azure リソースを作成します。 これらの手順を完了すると、Azure portal のリソース用の **[キー]** ページに、*サブスクリプション* キーが表示されます。

1. Azure portal にサインインし、[QnA Maker リソースを作成](https://ms.portal.azure.com/#create/Microsoft.CognitiveServicesQnAMaker)します。

1. 使用条件を読んだ後、 **[作成]** を選択します。

    ![新しい QnA Maker サービスの作成](../media/qnamaker-how-to-setup-service/create-new-resource-button.png)

1. **QnA Maker** で、[マネージド (プレビュー)] チェックボックスをオンにして、適切な層とリージョンを選択します。

    ![新しい QnA Maker マネージド サービスを作成する - 価格レベルとリージョン](../media/qnamaker-how-to-setup-service/enter-qnamaker-v2-info.png)

    * QnA Maker リソースのデプロイ先となる **サブスクリプション** を選択します。
    * この QnA Maker マネージド (プレビュー) リソースのデプロイ先として、新しい **リソース グループ** を作成する (推奨) か、既存のものを使用します。 QnA Maker マネージド (プレビュー) によって、いくつかの Azure リソースが作成されます。 これらのリソースを保持するリソース グループを作成すると、リソースの検索、管理、および削除を、リソース グループ名によって簡単に実行できます。
    * **[名前]** フィールドに、この QnA Maker マネージド (プレビュー) サービスを識別する一意の名前を入力します。 
    * QnA Maker マネージド (プレビュー) サービスをデプロイする **場所** を選択します。 管理 API とサービス エンドポイントは、この場所でホストされます。 
    * QnA Maker マネージド (プレビュー) サービス (プレビュー) の **[価格レベル]** を選択します (プレビューの場合は Free)。 [詳細については、SKU の価格](https://aka.ms/qnamaker-pricing)に関するページをご覧ください。
    * Azure Cognitive Search インデックスのデプロイ先となる **検索場所** を選択します。 顧客データをどの場所に格納する必要があるかの制限に基づいて、Azure Cognitive Search で使用する場所を選択できます。
    * Azure Cognitive Search サービスの **検索価格レベル** を選択します。 Free レベル オプションを利用できない (灰色表示されている) 場合、それは、ご利用のサブスクリプションで Free サービスが既にデプロイされていることを意味します。 その場合は、Basic レベルから開始する必要があります。 [Azure Cognitive Search の価格の詳細](https://azure.microsoft.com/pricing/details/search/)に関するページを参照してください。

1. すべてのフィールドを確認した後、 **[確認と作成]** を選択します。 プロセスが完了するまでに数分かかることがあります。

1. デプロイが完了すると、サブスクリプション内に次のリソースが作成されていることがわかります。

    ![新しい QnA Maker マネージド (プレビュー) サービスによって作成されたリソース](../media/qnamaker-how-to-setup-service/resources-created-v2.png)

    種類が _Cognitive Services_ であるリソースには、_サブスクリプション_ キーがあります。
    
---

## <a name="recommended-settings-for-network-isolation"></a>ネットワーク分離の推奨設定

# <a name="qna-maker-ga-stable-release"></a>[QnA Maker GA (安定版リリース)](#tab/v1)

1. [仮想ネットワークを構成](../../cognitive-services-virtual-networks.md?tabs=portal)して、Cognitive Services リソースをパブリック アクセスから保護します。
2. App Service (QnA Runtime) をパブリック アクセスから保護します。

   ##### <a name="add-ips-to-app-service-allowlist"></a>App Service 許可リストへの IP の追加

    * Cognitive Services IP からのトラフィックのみを許可します。 これらは、既にサービスタグ `CognitiveServicesManagement` に含まれています。 これは、オーサリング API シリーズ (KB の作成/更新) で App Service を起動し、それに応じて Azure Search Service を更新するために必要です。 [サービス タグに関する詳細](../../../virtual-network/service-tags-overview.md)を確認します。
    * Bot Service、QnA Maker ポータル (ご使用の企業ネットワークなど) のような他のエントリポイントも予測 "GenerateAnswer" API アクセスを許可していることを確認します。
    * IP アドレスの範囲を許可リストに追加するには、次の手順に従ってください。

      * [すべてのサービス タグの IP 範囲](https://www.microsoft.com/download/details.aspx?id=56519)をダウンロードします。
      * "CognitiveServicesManagement" の IP を選択します。
      * App Service リソースのネットワーク セクションに移動し、[アクセス制限の構成] をクリックして、許可リストに IP を追加します。

    また、App Service に対して同じ処理を行う自動スクリプトも用意されています。 [許可リストを構成するための PowerShell スクリプト](https://github.com/pchoudhari/QnAMakerBackupRestore/blob/master/AddRestrictedIPAzureAppService.ps1)については、GitHub 上にあります。 スクリプト パラメーターとして、サブスクリプション ID、リソース グループ、および実際の App Service 名を入力する必要があります。 スクリプトを実行すると、App Service の許可リストに IP が自動的に追加されます。

    ##### <a name="configure-app-service-environment-to-host-qna-maker-app-service"></a>QnA Maker App Service をホストするように App Service Environment を構成する
    App Service Environment (ASE) を使用して、QnA Maker App Service をホストできます。 次の手順に従ってください。

    1. App Service Environment を作成し、"外部" としてマークします。 手順については、[チュートリアル](../../../app-service/environment/create-external-ase.md)を参照してください。
    2.  App Service Environment 内に App Service を作成します。
        * App Service の構成を確認し、アプリケーション設定として "PrimaryEndpointKey" を追加します。 'PrimaryEndpointKey' の値は、“\<app-name\>-PrimaryEndpointKey” に設定されている必要があります。 アプリ名は、App Service の URL で定義されています。 たとえば、App Service の URL が "mywebsite.myase.p.azurewebsite.net" の場合、アプリ名は "mywebsite" になります。 この場合、'PrimaryEndpointKey' の値は “mywebsite-PrimaryEndpointKey” に設定されている必要があります。
        * Azure Search サービスを作成します。
        * Azure Search とアプリの設定が適切に構成されていることを確認します。 
          この[チュートリアル](../reference-app-service.md?tabs=v1#app-service)を参照してください。
    3.  App Service Environment に関連付けられているネットワーク セキュリティ グループを更新します。
        * 事前に作成された受信セキュリティ規則を要件に従って更新します。
        * ソースが 'Service Tag'、ソース サービス タグが 'CognitiveServicesManagement' の新しい受信セキュリティ規則を追加します。
    4.  Azure Resource Manager を使用して QnA Maker Cognitive Services インスタンス (Microsoft.CognitiveServices/accounts) を作成します。QnA Maker エンドポイントは上記で作成した App Service Environment (https:// mywebsite.myase.p.azurewebsite.net) に設定する必要があります。
    
3. Cognitive Search を VNET 内のプライベート エンドポイントとして構成する

    QnA Maker リソースの作成中に検索インスタンスが作成されるとき、完全に顧客の VNET 内に作成されたプライベート エンドポイント構成をサポートするよう Cognitive Search に強制することができます。

    プライベート エンドポイントを使用するには、すべてのリソースが同じリージョンに作成されている必要があります。

    * QnA Maker リソース
    * 新しい Cognitive Search リソース
    * 新しい Virtual Network リソース

    [Azure portal](https://portal.azure.com) で次の手順を実行します。

    1. [QnA Maker リソース](https://ms.portal.azure.com/#create/Microsoft.CognitiveServicesQnAMaker)を作成します。
    1. エンドポイント接続 (データ) が "_プライベート_" に設定された新しい Cognitive Search リソースを作成します。 このリソースは、手順 1. で作成した QnA Maker リソースと同じリージョンに作成します。 [Cognitive Search リソースの作成](../../../search/search-create-service-portal.md)について理解を深めてから、こちらのリンクを使用して[リソースの作成ページ](https://ms.portal.azure.com/#create/Microsoft.Search)に直接移動します。
    1. 新しい[仮想ネットワーク リソース](https://ms.portal.azure.com/#create/Microsoft.VirtualNetwork-ARM)を作成します。
    1. この手順の手順 1. で作成した App Service リソース上に VNET を構成します。
        1. 手順 2. で作成した新しい Cognitive Search リソース用に、Cognitive Search の IP アドレスへの新しい DNS エントリを VNET に作成します。 。
    1. 手順 2. で作成した[新しい Cognitive Search リソースに App Service を関連付け](#configure-qna-maker-to-use-different-cognitive-search-resource)ます。 その後は、手順 1. で作成した元の Cognitive Search リソースを削除してかまいません。

    [QnA Maker ポータル](https://www.qnamaker.ai/)で、初めてのナレッジ ベースを作成します。

# <a name="qna-maker-managed-preview-release"></a>[QnA Maker マネージド (プレビュー リリース)](#tab/v2)

1. [仮想ネットワークを構成](../../cognitive-services-virtual-networks.md?tabs=portal)して、Cognitive Services リソースをパブリック アクセスから保護します。
2. Azure Search リソースに[プライベート エンドポイントを作成](../reference-private-endpoint.md)します。

---

## <a name="upgrade-azure-resources"></a>Azure リソースのアップグレード

# <a name="qna-maker-ga-stable-release"></a>[QnA Maker GA (安定版リリース)](#tab/v1)

### <a name="upgrade-qna-maker-sku"></a>QnA Maker の SKU をアップグレードする

現在のレベルよりも多くの質問と回答をナレッジ ベースに含めたい場合は、QnA Maker サービスの価格レベルをアップグレードします。

QnA Maker 管理 SKU をアップグレードするには、次の手順に従います。

1. Azure portal の QnA Maker リソースに移動し、 **[価格レベル]** を選択します。

    ![QnA Maker リソース](../media/qnamaker-how-to-upgrade-qnamaker/qnamaker-resource.png)

1. 適切な SKU を選択し、 **[選択]** を押します。

    ![QnA Maker の価格](../media/qnamaker-how-to-upgrade-qnamaker/qnamaker-pricing-page.png)
    
### <a name="upgrade-app-service"></a>App Service をアップグレードする

ナレッジ ベースでクライアント アプリからのより多くの要求に対応する必要がある場合は、App Service の価格レベルをアップグレードします。

App Service は、[スケールアップ](../../../app-service/manage-scale-up.md)またはスケールアウトすることができます。

Azure portal で App Service リソースに移動し、必要に応じて **[スケールアップ]** と **[スケールアウト]** のどちらかのオプションを選択します。

![QnA Maker App Service のスケーリング](../media/qnamaker-how-to-upgrade-qnamaker/qnamaker-appservice-scale.png)

### <a name="upgrade-the-azure-cognitive-search-service"></a>Azure Cognitive Search サービスのアップグレード

多数のナレッジ ベースを使用する予定の場合は、Azure Cognitive Search サービスの価格レベルをアップグレードします。

現在、Azure Search SKU のインプレース アップグレードを実行することはできません。 ただし、必要な SKU で新しい Azure Search リソースを作成し、その新しいリソースにデータを復元して、QnA Maker スタックにリンクすることはできます。 そのためには、次の手順に従います。

1. Azure portal で新しい Azure Search リソースを作成し、必要な SKU を選択します。

    ![QnA Maker Azure Search リソース](../media/qnamaker-how-to-upgrade-qnamaker/qnamaker-azuresearch-new.png)

1. 元の Azure Search リソースのインデックスを新しいリソースに復元します。 [バックアップと復元のサンプル コード](https://github.com/pchoudhari/QnAMakerBackupRestore)を参照してください。

1. データが復元されたら、新しい Azure Search リソースに移動し、 **[キー]** を選択して、 **[名前]** と **[管理者キー]** を書き留めます。

    ![QnA Maker Azure Search キー](../media/qnamaker-how-to-upgrade-qnamaker/qnamaker-azuresearch-keys.png)

1. 新しい Azure Search リソースを QnA Maker スタックにリンクするために、QnA Maker App Service インスタンスに移動します。

    ![QnA Maker App Service インスタンス](../media/qnamaker-how-to-upgrade-qnamaker/qnamaker-resource-list-appservice.png)

1. **[アプリケーションの設定]** を選択し、 **[AzureSearchName]** フィールドと **[AzureSearchAdminKey]** フィールドを手順 3 で書き留めた値に変更します。

    ![QnA Maker App Service の設定](../media/qnamaker-how-to-upgrade-qnamaker/qnamaker-appservice-settings.png)

1. App Service インスタンスを再起動します。

    ![QnA Maker App Service インスタンスの再起動](../media/qnamaker-how-to-upgrade-qnamaker/qnamaker-appservice-restart.png)
    
### <a name="inactivity-policy-for-free-search-resources"></a>無料 Search リソースのアイドル時間ポリシー

QnA Maker リソースを使用していない場合、そのリソースをすべて削除してください。 不使用のリソースを削除しなかった場合、無料の Search リソースを作成したときにナレッジ ベースが機能しなくなります。

無料の Search リソースは、API 呼び出しを受信しない状態で 90 日経過すると削除されます。
    
# <a name="qna-maker-managed-preview-release"></a>[QnA Maker マネージド (プレビュー リリース)](#tab/v2)

### <a name="upgrade-the-azure-cognitive-search-service"></a>Azure Cognitive Search サービスのアップグレード

多数のナレッジ ベースを使用する予定の場合は、Azure Cognitive Search サービスの価格レベルをアップグレードします。

現在、Azure Search SKU のインプレース アップグレードを実行することはできません。 ただし、必要な SKU で新しい Azure Search リソースを作成し、その新しいリソースにデータを復元して、QnA Maker スタックにリンクすることはできます。 そのためには、次の手順に従います。

1. Azure portal で新しい Azure Search リソースを作成し、必要な SKU を選択します。

    ![QnA Maker Azure Search リソース](../media/qnamaker-how-to-upgrade-qnamaker/qnamaker-azuresearch-new.png)

1. 元の Azure Search リソースのインデックスを新しいリソースに復元します。 [バックアップと復元のサンプル コード](https://github.com/pchoudhari/QnAMakerBackupRestore)を参照してください。

1. 新しい Azure Search リソースを QnA Maker マネージド (プレビュー) サービスにリンクするには、次のトピックを参照してください。

### <a name="inactivity-policy-for-free-search-resources"></a>無料 Search リソースのアイドル時間ポリシー

QnA Maker リソースを使用していない場合、そのリソースをすべて削除してください。 不使用のリソースを削除しなかった場合、無料の Search リソースを作成したときにナレッジ ベースが機能しなくなります。

無料の Search リソースは、API 呼び出しを受信しない状態で 90 日経過すると削除されます。

---

## <a name="configure-azure-resources"></a>Azure リソースの構成

# <a name="qna-maker-ga-stable-release"></a>[QnA Maker GA (安定版リリース)](#tab/v1)

### <a name="configure-qna-maker-to-use-different-cognitive-search-resource"></a>別の Cognitive Search リソースを使用するように QnA Maker を構成する

ポータルを使用して QnA サービスとその依存関係 (Search など) を作成すると、Search サービスが自動的に作成され、QnA Maker サービスにリンクされます。 これらのリソースが作成された後、既存の Search サービスを使用するように App Service 設定を更新して、先ほど作成されたサービスを削除できます。

QnA Maker の **App Service** リソースには Cognitive Search リソースが使用されます。 QnA Maker に使用される Cognitive Search リソースを変更するには、Azure portal の設定を変更する必要があります。

1. QnA Maker で使用する Cognitive Search リソースの **管理者キー** と **名前** を取得します。

1. [Azure portal](https://portal.azure.com) にサインインし、QnA Maker リソースに関連付けられている **アプリ サービス** を見つけます。 両方とも同じ名前です。

1. **[設定]** 、 **[構成]** の順に選択します。 これで、QnA Maker の App Service の既存の設定がすべて表示されます。

    > [!div class="mx-imgBorder"]
    > ![App Service の構成設定を表示する Azure portal のスクリーンショット](../media/qnamaker-how-to-upgrade-qnamaker/change-search-service-app-service-configuration.png)

1. 次のキーの値を変更します。

    * **AzureSearchAdminKey**
    * **AzureSearchName**

1. 新しい設定を使用するには、アプリ サービス を再起動する必要があります。 **[概要]** を選択し、 **[再起動]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![構成設定の変更後に App Service を再起動する Azure portal のスクリーンショット](../media/qnamaker-how-to-upgrade-qnamaker/screenshot-azure-portal-restart-app-service.png)

Azure Resource Manager テンプレートを使用して QnA サービスを作成する場合は、すべてのリソースを作成し、既存の Search サービスを使用するように App Service の作成を制御できます。

詳しくは、App Service の[アプリケーションの設定](../../../app-service/configure-common.md#configure-app-settings)を構成する方法をご覧ください。

### <a name="get-the-latest-runtime-updates"></a>最新のランタイム更新プログラムを取得する

QnA Maker ランタイムは、Azure portal で [QnA Maker サービスを作成する](./set-up-qnamaker-service-azure.md)ときにデプロイされる Azure App Service インスタンスの一部です。 ランタイムの更新は定期的に行われます。 QnA Maker App Service インスタンスは、2019 年 4 月のサイト拡張リリース (バージョン 5+) 以降は自動更新モードになります。 この更新は、アップグレード中のダウンタイムがゼロになるように設計されています。

[https://www.qnamaker.ai/UserSettings](https://www.qnamaker.ai/UserSettings ) で現在のバージョンを確認できます。 ご使用のバージョンがバージョン 5.x よりも古い場合は、App Service を再起動して最新の更新プログラムを適用する必要があります。

1. [Azure portal](https://portal.azure.com) で QnA Maker サービス (リソース グループ) に移動します。

    > [!div class="mx-imgBorder"]
    > ![QnA Maker Azure リソース グループ](../media/qnamaker-how-to-troubleshoot/qnamaker-azure-resourcegroup.png)

1. App Service インスタンスをクリックして、 **[概要]** セクションを開きます。

    > [!div class="mx-imgBorder"]
    > ![QnA Maker App Service インスタンス](../media/qnamaker-how-to-troubleshoot/qnamaker-azure-appservice.png)


1. App Service を再起動します。 更新プロセスは数秒で完了します。 この再起動中、エンド ユーザーは、この QnA Maker サービスを使用する依存アプリケーションやボットを使用できなくなります。

    ![QnA Maker App Service インスタンスの再起動](../media/qnamaker-how-to-upgrade-qnamaker/qnamaker-appservice-restart.png)

### <a name="configure-app-service-idle-setting-to-avoid-timeout"></a>タイムアウトを回避するように App Service のアイドル設定を構成する

公開されたナレッジ ベースの QnA Maker 予測ランタイムを提供するアプリ サービスにはアイドル タイムアウトの構成があり、サービスがアイドル状態の場合、既定では自動的にタイムアウトします。 QnA Maker の場合、これは、予測ランタイム GenerateAnswer API は、一定期間トラフィックがないとタイムアウトする場合があることを意味します。

トラフィックがない場合でも、予測エンドポイント アプリが読み込まれたままにするには、アイドル状態を常時オンに設定します。

1. [Azure portal](https://portal.azure.com) にサインインします。
1. QnA Maker リソースの App Service を探して選択します。 名前は QnA Maker リソースと同じですが、App Service の **種類** は異なります。
1. **[設定]** を探し、 **[構成]** を選択します。
1. [構成] ペインで **[一般設定]** を選択して、 **[常にオン]** を探し、値として **[オン]** を選択します。

    > [!div class="mx-imgBorder"]
    > ![[構成] ペインの **[一般設定]** の **[常にオン]** を **[オン]** に設定する。](../media/qnamaker-how-to-upgrade-qnamaker/configure-app-service-idle-timeout.png)

1. **[保存]** を選んで構成を保存します。
1. アプリを再起動して新しい設定を使用するかどうかを確認するメッセージが表示されます。 **[続行]** をクリックします。

詳しくは、App Service の[一般設定](../../../app-service/configure-common.md#configure-general-settings)を構成する方法をご覧ください。

### <a name="business-continuity-with-traffic-manager"></a>トラフィック マネージャーを使用したビジネス継続性

ビジネス継続性計画の主な目的は、回復性に優れたナレッジ ベース エンドポイントを作成し、そのナレッジ ベース エンドポイントを使用するボットまたはアプリケーションにダウン タイムが発生しないようにすることです。

> [!div class="mx-imgBorder"]
> ![QnA Maker bcp 計画](../media/qnamaker-how-to-bcp-plan/qnamaker-bcp-plan.png)

上に示した概念の説明は次のとおりです。

1. [ペアになっている Azure リージョン](../../../best-practices-availability-paired-regions.md)に、同一の [QnA Maker サービス](set-up-qnamaker-service-azure.md)を 1 つずつ、計 2 つ設定します。

1. プライマリ QnA Maker App サービスを[バックアップ](../../../app-service/manage-backup.md)して、セカンダリ セットアップで[復元](../../../app-service/web-sites-restore.md)します。 これにより、両方のセットアップが同じホスト名とキーで動作するようになります。

1. プライマリとセカンダリの Azure 検索インデックスを常に同期しておきます。Azure のインデックスをバックアップおよび復元する方法については、[GitHub](https://github.com/pchoudhari/QnAMakerBackupRestore) でサンプルを参照してください。

1. [連続エクスポート](../../../azure-monitor/app/export-telemetry.md)を使って Application Insights をバックアップします。

1. プライマリとセカンダリのスタックを設定したら、[トラフィック マネージャー](../../../traffic-manager/traffic-manager-overview.md)を使用して 2 つのエンドポイントを構成し、ルーティング方法を設定します。

1. トラフィック マネージャーのエンドポイント向けに Transport Layer Security (TLS) (旧称は Secure Sockets Layer (SSL)) 証明書を作成する必要があります。 アプリ サービスで [TLS/SSL 証明書](../../../app-service/configure-ssl-bindings.md)をバインドします。

1. 最後に、ボットまたはアプリでトラフィック マネージャー エンドポイントを使用します。

# <a name="qna-maker-managed-preview-release"></a>[QnA Maker マネージド (プレビュー リリース)](#tab/v2)

### <a name="configure-qna-maker-managed-preview-service-to-use-different-cognitive-search-resource"></a>別の Cognitive Search リソースを使用するように QnA Maker マネージド (プレビュー) サービスを構成する

ポータルを使用して QnA マネージド (プレビュー) サービスとその依存関係 (Search など) を作成すると、Search サービスが自動的に作成され、QnA Maker マネージド (プレビュー) サービスにリンクされます。 これらのリソースが作成されたら、 **[構成]** タブで Search サービスを更新することができます。

1. Azure portal で QnA Maker マネージド (プレビュー) サービスにアクセスします。

1. **[構成]** を選択し、ご利用の QnA Maker マネージド (プレビュー) サービスとリンクさせる Azure Cognitive Search サービスを選択します。

    ![QnA Maker マネージド (プレビュー) の構成ページのスクリーンショット](../media/qnamaker-how-to-upgrade-qnamaker/change-search-service-configuration.png)

1. **[保存]** をクリックします。

> [!NOTE]
> QnA Maker に関連付けられている Azure Search サービスを変更した場合、既に存在しているすべてのナレッジ ベースにアクセスできなくなります。 Azure Search サービスを変更する前に、既存のナレッジ ベースがエクスポートされていることを確認してください。

---

## <a name="delete-azure-resources"></a>Azure リソースを削除する

QnA Maker ナレッジ ベースに使用されているいずれかの Azure リソースを削除すると、ナレッジ ベースは機能しなくなります。 いずれかのリソースを削除する前に、 **[設定]** ページから確実にナレッジ ベースをエクスポートしてください。

## <a name="next-steps"></a>次のステップ

[App Service](../../../app-service/index.yml) と [Search Service](../../../search/index.yml) の詳細をご覧ください。

> [!div class="nextstepaction"]
> [他のユーザーとの作成方法の詳細をご覧ください](../index.yml)
