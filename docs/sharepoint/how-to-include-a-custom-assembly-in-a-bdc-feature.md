---
title: 如何：在 BDC 功能中包含自訂群組件 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 772cdbaca67cc82fc6b7eb2c5ef5adb6508df34a
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015256"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>如何：在 BDC 功能中包含自訂群組件
  您的專案可以參考相同方案中其他專案的元件。 不過，您必須使用 [**將參考的元件指派給 type lobsystems** ] 對話方塊，將這些元件加入至專案的功能檔案。

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>若要在商務資料連線（BDC）功能中包含自訂群組件

1. 在 [**方案總管**中，選擇包含 BDC 模型的資料夾。

2. 在 [檢視] **** 功能表上，按一下 [屬性視窗] ****。

3. 在 [**屬性**] 視窗中，依序選擇 [**元件**] 屬性和省略號按鈕（[![ASP.NET Mobile 設計](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")工具] [橢圓形]）。

     [將**參考的元件指派給 type lobsystems** ] 對話方塊隨即出現。

4. 在 [**選取元件**] 清單中，選擇 [自訂群組件]。

    > [!NOTE]
    > 如果您已加入包含元件之專案的參考，則元件只會出現在 [**指派參考的元件至 type lobsystems** ] 對話方塊中。 如需詳細資訊，請參閱[如何：使用加入參考對話方塊加入或移除參考](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)。

5. 在 [**參考屬性**] 群組中，開啟針對 [ **LobSystem 範圍**] 屬性顯示的清單，選擇使用自訂群組件之方法的 LOB 系統，然後選擇 [**確定]** 按鈕。

    > [!NOTE]
    > 若要在自訂群組件中偵錯工具代碼，您必須將元件加入至方案套件。 如需詳細資訊，請參閱[如何：新增和移除其他元件](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。

## <a name="see-also"></a>另請參閱
- [如何：使用資源檔來指定當地語系化名稱、屬性和許可權](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [如何：將現有的 BDC 模型檔案加入至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)
- [如何：建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)
- [將商務資料 Integragte 到 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
