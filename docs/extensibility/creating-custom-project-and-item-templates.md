---
title: 建立自定義項目和項目範本 |微軟文件
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae404004f2660048ef7581a661d8f785495ed95a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739448"
---
# <a name="create-custom-project-and-item-templates"></a>建立自訂項目與專案樣本

Visual Studio SDK 包括創建自定義專案範本的專案範本和自定義專案範本。 這些範本包括一些常見的參數替換,並生成為 zip 檔。 它們不是自動部署的,並且在實驗實例中不可用。 您必須將產生的 zip 檔案複製到使用者範本目錄。

樣本創建範本允許您在較大的擴展中包含範本。 這允許您在源檔上實現版本控制,並將一組範本專案構建到一個 VSIX 套件中。

您還可以配置範本以安裝 NuGet 套件。 有關詳細資訊,請參閱[Visual Studio 樣本中的 NuGet 套件](/nuget/visual-studio-extensibility/visual-studio-templates)。

對於基本範本創建方案,應使用**匯出範本**嚮導,該嚮導輸出到壓縮檔。 有關基本範本建立的詳細資訊,請參閱[建立項目和專案範本](../ide/creating-project-and-item-templates.md)。

> [!NOTE]
> 從 Visual Studio 2017 開始,將不再執行自定義專案和專案範本的掃描。 相反,擴展必須提供描述這些範本的安裝位置的範本清單檔。 您可以使用 Visual Studio 2017 更新 VSIX 擴展。 如果使用 MSI 部署副檔名,則必須手動生成範本清單檔。 有關詳細資訊,請參閱為[Visual Studio 2017 升級自訂項目和專案範本](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)。 範本清單架構記錄在[可視化工作室範本清單架構引用](../extensibility/visual-studio-template-manifest-schema-reference.md)中。

## <a name="create-a-project-template"></a>建立專案範本

1. 創建專案範本專案。 您可以通過搜尋「項目範本」並選擇 C# 或 Visual Basic 版本,在 **「新專案**」對話框中找到專案範本。

     該範本生成類檔、圖示 *、.vstemplate*檔、名為*ProjectTemplate.vbproj*或*ProjectTemplate.csproj*的可編輯專案檔,以及一些通常由其他專案類型(如*資源.resx*檔 *、AssemblyInfo*檔和 *.settings*檔)生成的檔。 每個代碼檔都包含常見的參數替換(如果適用)。

![專案樣本項目選擇](media/project-template-selection.png)

2. 根據專案需要從專案添加和刪除專案。 不要刪除可編輯的專案檔 *、AssemblyInfo*檔案或 *.vstemplate*檔案。

3. 更新 *.vstemplate*檔以反映任何添加和刪除。 [項目](../extensibility/project-element-visual-studio-templates.md)元素必須包含要包含在範本中的每個檔的[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)元素。

4. 修改代碼檔和其他面向用戶的內容,並添加適當的參數替換。

5. 根據需要修改生成的內容。

6. 建置專案。

     Visual Studio 建立包含範本的 *.zip*檔案。 它不部署,並且在實驗實例中不可用。

## <a name="create-an-item-template"></a>建立項目範本

1. 創建專案範本專案。

     該範本生成類檔、圖示 *、.vstemplate*檔和*AssemblyInfo*檔案。 類檔包含一些常見的參數替換。

2. 根據專案需要從專案添加和刪除專案。

3. 更新 *.vstemplate*檔以反映任何添加和刪除。 [項目](../extensibility/project-element-visual-studio-templates.md)元素必須包含要包含在範本中的每個檔的[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)元素。

4. 修改代碼檔和其他面向用戶的內容,並添加適當的參數替換。

5. 根據需要修改生成的內容。

6. 建置專案。

     Visual Studio 會創建包含範本的壓縮檔。 它不部署,並且在實驗實例中不可用。

## <a name="deployment"></a>部署

### <a name="to-deploy-the-project-or-item-template"></a>部署項目或項目樣本

1. 建立 VSIX 專案。 有關詳細資訊,請參閱[VSIX 專案樣本](../extensibility/vsix-project-template.md)。

2. 將 VSIX 專案設置為啟動專案。 在**解決方案資源管理器**中,選擇 VSIX 專案節點,右鍵單擊,然後選擇「**設定為啟動專案**」 。。

3. 將專案範本專案設置為 VSIX 專案的資產。 打開 *.vsix清單*檔。 轉到「**資產**」選項卡,然後按**下 「新建**」。。

    1. 將**型態「 字**段設定為**Microsoft.VisualStudio.ProjectTemplate**或**Microsoft.VisualStudio.ItemTemplate**.

    2. 對於源,選擇**當前解決方案選項中的 A 專案**,然後選擇包含範本的專案。

4. 產生解決方案,然後按**F5**。 出現實驗實例。

5. 對於專案範本專案,您應該在 Visual C# 或 Visual Basic 節點中看到**新項目**對話框(**檔案** > **新專案** > **)中**列出的專案範本。 對於專案範本專案,您應該會看到「**添加新項目**」對話方塊中列出的專案範本。 要查看「**添加新項目**」對話框,請從**解決方案資源管理器中選擇**專案節點,然後按一下「**新增新** > **項**」。

## <a name="see-also"></a>另請參閱

- [視覺化工作室範本參考](../ide/creating-project-and-item-templates.md)
- [視覺工作室樣本中的 NuGet 套件](/nuget/visual-studio-extensibility/visual-studio-templates)
