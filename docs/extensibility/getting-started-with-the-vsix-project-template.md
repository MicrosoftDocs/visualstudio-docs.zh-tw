---
title: 開始使用 VSIX 項目樣本 ( 1) :微軟文件
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 773e9e6891599cd9672888d0521e94891e0d9f41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711237"
---
# <a name="get-started-with-the-vsix-project-template"></a>開始使用 VSIX 專案樣本

您可以使用 VSIX 專案範本建立擴充或打包現有擴展進行部署。 VSIX 專案範本同時具有可視化基本版和可視化 C++ 版本,並作為可視化工作室 SDK 的一部分安裝。

 VSIX 專案範本僅包含一個*source.擴展.vsix清單*檔,該檔包含有關擴展及其提供的資產的資訊。

 要查找 VSIX 專案範本,必須安裝可視化工作室 SDK。 有關詳細資訊,請參閱[可視化工作室 SDK](../extensibility/visual-studio-sdk.md)。

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>使用 VSIX 專案樣本部署自訂項目樣本

 以下步驟演示如何使用 VSIX 專案打包專案範本,以便與其他開發人員共用或上傳到可視化工作室庫。

1. 創建專案範本。

    1. 打開從中創建範本的專案。 此專案可以是任何項目類型。

    2. 按一下 [專案]**** 功能表上的 [匯出範本]****。 完成嚮導的步驟。

         *.zip*檔案以 *%USERPROFILE%%\我的文件\視覺化工作室[版本]建立[我的匯出範\\本*] 。

2. 創建空 VSIX 專案。

     選擇 **「檔案** > **新專案** > **」。** 在搜尋框中,鍵入"vsix"並選擇**VSIX 專案的** **C#** 或**可視基本**版本。

3. 將 *.zip*檔案添加到專案中。 複製**到輸出目錄屬性**設定為`Copy Always`。

4. 在**解決方案資源管理員**中,按兩下*source.延伸.vsixmanifest*檔案以在**VSIX 清單設計器**中開啟該檔案,然後進行以下變更:

    - 將**產品名稱**欄位設置為 **「我的項目範本**」。

    - 將**產品 ID**欄位設置為 **「我的項目範本 - 1」。**

    - 將 **「作者」** 欄位設定為**法布裡卡姆**。

    - 將 **「描述」** 欄位設定為 **「我的項目範本**」 。

    - 在 **"資產"** 部分中,添加**Microsoft.VisualStudio.ProjectTemplate**類型,並將其路徑設置為 *.zip*檔的名稱。

5. 保存並關閉*源.擴展.vsixmanifest*檔案。

6. 建置專案。

7. 在輸出目錄中,按兩下 *.vsix*檔。

8. 將顯示**一個 VSIX 安裝程式**訊息框。 按照說明安裝擴展。

9. 結束再重新開啟 Visual Studio。

::: moniker range="vs-2017"

10. 選擇**延伸和更新**(在 **"工具"** 選單上),然後選擇 **「範本」** 類別。 可用擴展之一應該是 **「我的項目範本**」。

::: moniker-end

::: moniker range=">=vs-2019"

10. 選擇 **「管理延伸**」(在 **"擴展"** 選單上),然後選擇 **「範本」** 類別。 可用擴展之一應該是 **「我的項目範本**」。

::: moniker-end

11. 新項目範本顯示在與原始專案範本相同的新**專案"** 對話方塊中。 例如,如果從可視化基本主控台應用程式創建了名為**VB 控制台**的範本,則**VB 控制台**將顯示在與可視化基本**控制台應用程式**樣本相同的窗格中。

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>在「新項目」對話框中指定範本的位置

1. 樣本目錄位於 *[視覺工作室安裝路徑][通用 7_IDE_專案範本*和 *[視覺工作室安裝路徑]_Common7_IDE_ItemTemplates*目錄中。 **"新項目'** 對話框中頂級部分的名稱與範本資料夾的名稱不完全符合。 如果它們不同,請使用範本資料夾的名稱。

    將 *.vsix*檔案副檔名更改為 *.zip,* 然後打開該檔。

2. 創建與範本應出現在的 **「新專案」** 對話方塊中具有相同名稱的新資料夾。

3. 如果範本要出現在子節中,請創建同名子資料夾。

4. 將樣本 *.zip*檔案移動到新資料夾中。

5. 將 *.zip*延伸變更為 *.vsix*。

6. 打開 VSIX 清單。

7. 在 VSIX 清單中,更新範本**的資產**路徑,以便它指向包含範本檔的目錄樹的根目錄。 例如,如果範本位於 *[CSharp]Windows*中,則引用應指向 *_CSharp*。
