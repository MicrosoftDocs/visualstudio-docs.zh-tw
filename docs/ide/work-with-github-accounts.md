---
title: 在 Visual Studio 中使用 GitHub 帳戶
ms.date: 11/16/2020
ms.custom: ''
ms.topic: conceptual
description: 瞭解如何搭配使用 Visual Studio 與 GitHub 帳戶。
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9f55a233cc2550cd452851edc9092b4b2f4f2411
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296361"
---
# <a name="work-with-github-accounts-in-visual-studio"></a>在 Visual Studio 中使用 GitHub 帳戶

如果您有公用 GitHub 或 GitHub Enterprise 帳戶，您可以將它新增至您的 Visual Studio keychain。 新增您的帳戶之後，您就可以直接從 Visual Studio 存取和建立 GitHub 儲存機制，以利用平臺整合。

## <a name="adding-public-github-accounts"></a>新增公用 GitHub 帳戶

如果您已使用 Microsoft 帳戶或工作或學校帳戶登入 Visual Studio，則可以新增您的公用 GitHub 帳戶。

1. 在 Visual Studio 環境的右上角選取具有您姓名縮寫的圖示。 然後，選取 [ **帳戶設定** ]，以管理您的帳戶。 您也可以前往 [檔案  >  **帳戶設定**] 開啟 [帳戶設定] 對話方塊。

    :::image type="content" source="../ide/media/account-picker.png" alt-text="帳戶設定":::

2. 在 [ **所有帳戶** ] 子功能表下，選取加號以新增帳戶，然後選取 [ **GitHub**]。

    :::image type="content" source="../ide/media/sign-in-add-github.png" alt-text="選取 [新增 GitHub 帳戶]":::

3. 系統會將您重新導向至瀏覽器，您可以在其中使用您的 GitHub 認證登入。 登入之後，您將會在瀏覽器中收到成功的視窗，而且您可以回到 Visual Studio。

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="瀏覽器中的成功視窗":::

4. 您將會有兩個帳戶都出現在 [ **所有帳戶** ] 子功能表中。

    :::image type="content" source="../ide/media/show-both-accounts.png" alt-text="這兩個帳戶顯示":::

如果您尚未使用不同的帳戶登入 Visual Studio，請選取 Visual Studio 環境右上角的 [登 **入** ] 連結。 您也可以前往 [檔案  >  **帳戶設定**] 開啟 [帳戶設定] 對話方塊。 然後，遵循上面的指示來新增您的 GitHub 帳戶。

![未登入使用者](../ide/media/vs2019_usernotsignedin.png)

## <a name="adding-github-enterprise-accounts"></a>新增 GitHub enterprise 帳戶

根據預設，Visual Studio 只會啟用公用 GitHub 帳戶。

1. 若要啟用 GitHub enterprise 帳戶，請移至 [**工具**  >  **選項**]，並搜尋 **帳戶** 選項。

    :::image type="content" source="../ide/media/accounts-options.png" alt-text="帳戶選項功能表":::

2. 然後，選取要 **包含 GitHub Enterprise 伺服器帳戶** 的方塊。 下次您移至您的 **帳戶設定** ，並嘗試新增 github 帳戶時，您會看到 github 和 GitHub Enterprise 的選項。

    :::image type="content" source="../ide/media/github-enterprise-endpoint-signin.png" alt-text="使用 GitHub Enterprise 登入":::

3. 輸入您的 GitHub Enterprise 伺服器位址後，請選取 [ **使用您的瀏覽器登入**]。 您可以使用 GitHub Enterprise 認證登入。

## <a name="see-also"></a>另請參閱

- [Work with multiple user accounts](work-with-multiple-user-accounts.md)
- [登入 Visual Studio](signing-in-to-visual-studio.md)
