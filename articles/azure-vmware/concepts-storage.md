---
title: 概念 - ストレージ
description: Azure VMware Solution プライベート クラウドの主なストレージ機能について説明します。
ms.topic: conceptual
ms.date: 02/02/2021
ms.openlocfilehash: 522e4f651b36532ac0c144b3889b2b67c91dc77b
ms.sourcegitcommit: 44188608edfdff861cc7e8f611694dec79b9ac7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2021
ms.locfileid: "99536952"
---
#  <a name="azure-vmware-solution-storage-concepts"></a>Azure VMware Solution のストレージの概念

Azure VMware Solution のプライベート クラウドは、ネイティブのクラスター全体のストレージに VMware vSAN を提供します。 クラスター内の各ホストのローカル ストレージはすべて、vSAN データストアで使用されます。また、保存データの暗号化は既定で使用可能で、有効になっています。 Azure Storage のリソースを使用すると、プライベート クラウドのストレージ機能を拡張できます。

## <a name="vsan-clusters"></a>vSAN クラスター

各クラスター ホスト内のローカル ストレージは、vSAN データストアの一部として使用されます。 すべてのディスクグループでは、1.6 TB の NVMe キャッシュ階層と共に、ホストあたり、生の SSD ベースの容量 15.4 TB が使用されます。 クラスターの生の容量階層のサイズは、ホストごとの容量にホストの数を掛けたものになります。 たとえば、4 つのホストで構成されたクラスターの場合、vSAN 容量階層で生の容量が 61.6 TB になります。

クラスター ホスト内のローカル ストレージは、クラスター全体の vSAN データストアで使用されます。 すべてのデータストアは、プライベート クラウドのデプロイの一環として作成され、すぐに使用できるようになります。 cloudadmin ユーザーと CloudAdmin グループ内のすべてのユーザーは、次の vSAN 権限を使用してデータストアを管理できます。
- Datastore.AllocateSpace
- Datastore.Browse
- Datastore.Config
- Datastore.DeleteFile
- Datastore.FileManagement
- Datastore.UpdateVirtualMachineMetadata

## <a name="data-at-rest-encryption"></a>保存データの暗号化

vSAN データストアでは、既定で保存データの暗号化が使用されます。 この暗号化ソリューションは KMS ベースで、キーの管理のために vCenter の操作をサポートしています。 キーは暗号化された状態で保存され、Azure Key Vault マスター キーによってラップされています。 なんらかの理由でホストがクラスターから削除されると、SSD 上のデータはすぐに無効になります。

## <a name="scaling"></a>Scaling

ネイティブのクラスター ストレージ容量は、クラスターにホストを追加することでスケーリングされます。 HE ホストを使用するクラスターの場合、クラスター全体の生の容量は、ホストが追加されるごとに 15.4 TB ずつ増加します。 GP ホストを使用して構築されたクラスターでは、ホストが追加されるごとに生の容量が 7.7 TB ずつ増加します。 どちらの種類のクラスターでも、クラスターにホストを追加するには約 10 分かかります。 クラスターのスケーリング手順については、[プライベート クラウドのスケーリングに関するチュートリアル][tutorial-scale-private-cloud]のページを参照してください。

## <a name="azure-storage-integration"></a>Azure ストレージの統合

プライベート クラウドで実行されているワークロードでは Azure のストレージ サービスを使用できます。 Azure のストレージ サービスには、ストレージ アカウント、Table Storage、Blob Storage が含まれています。 ワークロードを Azure のストレージ サービスに接続する際は、インターネットを経由しません。 この接続により、セキュリティが強化され、プライベート クラウドのワークロードで SLA ベースの Azure のストレージ サービスを使用できるようになります。

## <a name="next-steps"></a>次のステップ

Azure VMware Solution ストレージに関する概念を理解したら、次の事項の学習に進むことができます。

- [プライベート クラウドの ID の概念](concepts-identity.md)
- [Azure VMware Solution の vSphere ロールベースのアクセス制御](concepts-role-based-access-control.md)
- [Azure VMware Solution リソースを有効にする方法](enable-azure-vmware-solution.md)

<!-- LINKS - external-->

<!-- LINKS - internal -->
[tutorial-scale-private-cloud]: ./tutorial-scale-private-cloud.md
[concepts-identity]: ./concepts-identity.md
