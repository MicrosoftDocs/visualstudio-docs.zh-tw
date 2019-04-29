---
title: 開始使用 VSIX 專案範本 |Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6176fda41b16a092b52e83e0ce894e1d1898e0a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62911878"
---
# <a name="get-started-with-the-vsix-project-template"></a>開始使用 VSIX 專案範本

若要建立擴充功能或封裝部署的現有擴充功能，您可以使用 [VSIX 專案] 範本。 VSIX 專案範本有 Visual Basic 和 Visual C# 版本，並已安裝 Visual Studio SDK 的一部分。

 VSIX 專案範本只包含*source.extension.vsixmanifest*檔案，其中包含附隨的延伸模組和資產的相關資訊。

 若要尋找 VSIX 專案範本，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>部署自訂專案範本，使用 VSIX 專案範本

 下列步驟示範如何使用 VSIX 專案封裝專案範本，您可以與其他開發人員共用，或上傳至 Visual Studio 組件庫。

1. 建立專案範本。

    1. 開啟要從中建立範本的專案。 此專案可以是任何專案類型。

    2. 按一下 [專案] 功能表上的 [匯出範本]。 完成精靈的步驟。

         A *.zip*中建立檔案時 *%USERPROFILE%\My Documents\Visual Studio {version} \My Exported Templates\\*。

2. 建立空的 VSIX 專案。

     選取 [檔案]  >  [新增]  >  [專案]。 在 [搜尋] 方塊中，輸入 「 vsix"，然後選取**C#** 或是**Visual Basic**版本**VSIX 專案**。

3. 新增 *.zip*檔案加入專案。 設定其**複製到輸出目錄**屬性設`Copy Always`。

4. 在 **方案總管**，按兩下*source.extension.vsixmanifest*中開啟該檔案**VSIX 資訊清單設計工具**，然後進行下列變更：

    - 設定**Product Name**欄位設為**我的專案範本**。

    - 設定**產品識別碼**欄位設為**MyProjectTemplate-1**。

    - 設定**作者**欄位設為**Fabrikam**。

    - 設定**描述**欄位設為**我的專案範本**。

    - 在 **資產**區段中，新增**Microsoft.VisualStudio.ProjectTemplate**輸入，然後設定其路徑的名稱 *.zip*檔案。

5. 儲存並關閉*source.extension.vsixmanifest*檔案。

6. 建置專案。

7. 在輸出目錄中，按兩下 *.vsix*檔案。

8. A **VSIX 安裝程式**訊息方塊隨即出現。 請依照下列指示來安裝擴充功能。

9. 結束再重新開啟 Visual Studio。

::: moniker range="vs-2017"

10. 選取 **擴充功能和更新**(在**工具**功能表)，然後選取**範本**類別目錄。 其中一個可用的擴充功能應該**我的專案範本**。

::: moniker-end

::: moniker range=">=vs-2019"

10. 選取**管理延伸模組**(在**擴充功能**功能表)，然後選取**範本**類別目錄。 其中一個可用的擴充功能應該**我的專案範本**。

::: moniker-end

11. 新的專案範本會出現在**新的專案**與原始的專案範本相同的位置中的對話方塊。 比方說，如果您建立名為的範本**VB 主控台**Visual Basic 主控台應用程式中，從**VB 主控台**會出現在 Visual Basic 為同一個窗格**主控台應用程式**範本。

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>若要在新的 [專案] 對話方塊中指定的範本位置

1. 範本資料夾放 *{Visual Studio 安裝路徑} \Common7\IDE\ProjectTemplates*並 *{Visual Studio 安裝路徑} \Common7\IDE\ItemTemplates*目錄。 中的最上層的區段名稱**新的專案**對話方塊不完全相符的範本資料夾的名稱。 它們之間的差異，使用範本資料夾的名稱。

    變更 *.vsix*檔案以副檔名 *.zip*，然後開啟檔案。

2. 建立新的資料夾與名稱相同的區段**新的專案**範本應該會出現在對話方塊。

3. 如果範本才會出現在子區段中，建立具有相同名稱的子資料夾。

4. 將範本移 *.zip*檔案放置於新的資料夾。

5. 變更 *.zip*延伸模組 *.vsix*。

6. 開啟 VSIX 資訊清單。

7. 在 VSIX 資訊清單中，更新**資產**範本，讓它指向包含範本檔案的目錄樹狀結構根的路徑。 例如，如果範本位於*\CSharp\Windows*，參考應該指向*\CSharp*。
