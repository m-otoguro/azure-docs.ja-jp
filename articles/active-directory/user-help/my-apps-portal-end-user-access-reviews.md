---
title: アプリとグループへの組織のアクセスを管理する - Azure AD
description: マイ アプリ ポータルから組織のアプリとグループへのセキュリティ アクセスを管理するためにアクセス レビューを実行する方法について説明します。
services: active-directory
author: curtand
manager: daveba
ms.service: active-directory
ms.subservice: user-help
ms.workload: identity
ms.topic: end-user-help
ms.date: 10/19/2020
ms.author: curtand
ms.reviewer: kasimpso
ms.custom: user-help, seo-update-azuread-jan
ms.openlocfilehash: 8da9e97aaa2c6d99990df4221d8b6e99ab18ac83
ms.sourcegitcommit: 857859267e0820d0c555f5438dc415fc861d9a6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93124814"
---
# <a name="perform-an-access-review-from-the-my-apps-portal"></a>My Apps ポータルからアクセス レビューを実行する

職場または学校アカウントを Web ベースの **マイ アプリ** ポータルで使用して、アプリとグループのアクセス レビューを実行できます。 アクセス レビューを使用すると、期限切れのアクセスやアクセス要件の変化を管理し、それらが確認および更新されるようにすることができます。

**マイ アプリ** ポータルにアクセスできない場合は、ヘルプデスクに連絡してアクセス許可を得てください。

[!INCLUDE [preview-notice](../../../includes/active-directory-end-user-my-apps-portal.md)]

>[!Important]
>このコンテンツは、 **マイ アプリ** のユーザーを対象としています。 管理者の方は、「[アプリケーション管理のドキュメント](../manage-apps/index.yml)」で、クラウドベースのアプリの設定と管理の方法を詳しくご覧いただけます。

## <a name="manage-access-reviews"></a>アクセス レビューを管理する

自身のアクセス レビューを実行するアクセス許可を管理者から与えられている場合は、 **マイ アプリ** ポータル ページの **[アクセス レビュー]** タイルから、グループまたはアプリ アクセスを管理できます。

>[!Note]
>**[アクセス レビュー]** タイルが表示されない場合は、アクセス レビューを実行するアクセス許可がないか、承認を待っている保留中のレビューがないことを意味します。 タイルへのアクセス権が必要な場合は、ヘルプ デスクにお問い合わせください。

## <a name="to-perform-your-access-reviews"></a>自分のアクセス レビューを実行するには

1. 職場または学校のアカウントにサインインします。

2. Web ブラウザーを開いて https://myapps.microsoft.com に移動するか、組織から与えられたリンクを使用します。 たとえば、 https://myapps.microsoft.com/contoso.com など、組織のカスタマイズされたページに転送されることがあります。

    **[アプリ]** ページが表示され、組織が所有し、お客様が利用できるクラウドベースのアプリがすべて示されます。

    ![マイ アプリ ポータルの [アプリ] ページ](media/my-apps-portal/my-apps-home.png)

3. **[アクセス レビュー]** タイルを選択して、承認を待機しているアクセス レビューの一覧を表示します。

    ![保留中の組織のアクセス レビューを示した [アクセス レビュー] ページ](media/my-apps-portal/my-apps-portal-access-reviews-page.png)

4. **[レビューの開始]** を選択してアクセス レビューを開始します。

5. アクセスをレビューし、まだ必要かどうかを判断します。

    ![[レビューの開始] ページ、レビューの詳細を表示](media/my-apps-portal/my-apps-portal-perform-access-reviews-page.png)

    >[!Note]
    >管理者であり、グループまたはアプリへの組織のアクセスをレビューできる場合は、別のページが表示されます。 組織のグループまたはアプリのレビューの詳細については、[Azure AD アクセス レビューでのグループまたはアプリケーションへのアクセスのレビュー](../governance/perform-access-review.md)に関するページを参照してください。

6. **[はい]** を選択してアクセスを維持するか、 **[いいえ]** を選択してアクセスを削除します。

    **[はい]** を選択する場合は、 **[理由]** ボックスに正当性を指定する必要がある場合があります。

    ![[アクセス レビュー] ページ、サンプル テキストを含む [理由] ボックスを表示](media/my-apps-portal/my-apps-portal-perform-access-reviews-reason-box.png)

7. **[Submit]\(送信\)** をクリックします。

    アクセス レビューが完了し、 **[マイ アプリ]** ポータルに戻ります。

    >[!Note]
    >アクセス レビュー期間が終了するまで、いつでもアクセスを変更できます。 アプリまたはグループへのアクセスを削除しても、すぐには削除されません。 削除は、アクセス レビュー期間が終了したとき、または管理者がレビューを閉じたときに行われます。

## <a name="next-steps"></a>次のステップ

- [マイ アプリ ポータルでアプリにアクセスして使用する](my-apps-portal-end-user-access.md)
- [プロファイルの情報を変更する](./my-account-portal-settings.md)
- [グループ関連の情報を表示し、更新する](my-apps-portal-end-user-groups.md)