---
title: HOW TO：在 BDC 功能中包含自訂組件 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 6de3313dad06c009244a8b784e81bf7d2a768c3b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443121"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>HOW TO：在 BDC 功能中包含自訂組件
  您的專案可以參考組件，從相同的方案中其他專案。 不過，您必須將這些組件加入功能檔的專案使用**指派參考組件 Lobsystem**  對話方塊。

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>若要納入的商務資料連接 (BDC) 功能的自訂組件

1. 在 [**方案總管] 中**，選擇包含 BDC 模型的資料夾。

2. 在 [ **檢視** ] 功能表中，按一下 [ **屬性視窗**]。

3. 在 **屬性**] 視窗中，選擇**組件**屬性，然後按一下 省略符號按鈕 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile設計工具橢圓形"))。

     **指派參考組件 Lobsystem**  對話方塊隨即出現。

4. 在 **選取的組件**清單中，選擇自訂組件。

    > [!NOTE]
    > 組件才會出現在**指派參考組件 Lobsystem**對話方塊中，如果您已新增至專案，其中包含組件的參考。 如需詳細資訊，請參閱[如何：新增或移除參考使用加入參考對話方塊](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)。

5. 在 **參考屬性**群組中，開啟清單中所顯示**LobSystem 範圍**屬性，選擇 LOB 系統的方法，使用自訂的組件，然後選擇  **確定**  按鈕。

    > [!NOTE]
    > 偵錯自訂組件中的程式碼，您必須新增至方案套件的組件。 如需詳細資訊，請參閱[如何：新增和移除其他組件](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。

## <a name="see-also"></a>另請參閱
- [如何：使用資源檔來指定當地語系化的名稱、 屬性和權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [如何：將現有的 BDC 模型檔案新增至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [建立 business data connectivity 模型](../sharepoint/creating-a-business-data-connectivity-model.md)
- [如何：建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)
- [Integragte 到 SharePoint 的商務資料](../sharepoint/integrating-business-data-into-sharepoint.md)
