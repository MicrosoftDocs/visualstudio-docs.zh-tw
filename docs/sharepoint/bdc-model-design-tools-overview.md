---
title: BDC 模型設計工具總覽 |Microsoft Docs
description: 閱讀使用 (BDC) 模型的商務資料連線所要使用的設計工具總覽。 深入瞭解 BDC 設計工具、BDC 方法詳細資料視窗和 BDC Explorer。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b398d9c00caf3a4fa2ca58bafa3273673a305859
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851682"
---
# <a name="bdc-model-design-tools-overview"></a>BDC 模型設計工具總覽
  您可以使用 [BDC 設計工具]、[ **Bdc 方法詳細資料** ] 視窗和 [ **bdc Explorer**]，來設計 (Bdc) 模型的商務資料連線。

 **BDC Explorer** 可讓您流覽模型、搜尋模型，以及定義型別描述項。

## <a name="bdc-designer"></a>BDC 設計工具
 BDC 設計工具可讓您在模型中定義實體，並以視覺化方式排列彼此的關聯性。 使用 BDC 設計工具來完成下列工作：

- 將實體新增至模型。

- 從模型中移除實體。

- 定義實體之間的關聯性。

  若要開啟 BDC 設計工具，請按兩下專案中的模型檔案，或開啟模型檔案的快捷方式功能表，然後選擇 [ **開啟**]。 將實體從 [**工具箱**] 拖曳或複製到設計工具，以 **將實體新增** 至模型。 若要建立兩個實體之間的關聯，請選擇 [**工具箱**] 中的 [**關聯**] 控制項，選擇第一個實體，然後選擇第二個實體。

## <a name="bdc-method-details-window"></a>BDC 方法詳細資料視窗
 使用 [ **BDC 方法詳細資料** ] 視窗，即可定義方法的參數、實例和篩選描述項。

 您可以在 [ **BDC 方法詳細資料** ] 視窗中快速產生搜尋工具、特定搜尋工具、建立者、更新程式和刪除者方法。 當您產生這些方法時，Visual Studio 會將中繼資料（例如參數、實例和類型描述元）加入至方法。 您可以修改此中繼資料以滿足您的特定案例。

 若要開啟 [ **BDC 方法詳細資料**] 視窗，請在功能表列上，選擇 [**查看**  >  **其他 Windows**  >  **BDC 方法詳細資料**]。

 若要在 [ **Bdc 方法詳細資料** ] 視窗中查看方法，請選擇 bdc 設計工具中的實體。 所選實體的方法會出現在 [ **BDC 方法詳細資料** ] 視窗中。 如果您沒有在 BDC 設計工具中選擇實體，[ **Bdc 方法詳細資料** ] 視窗就不會顯示任何資訊。

 展開或折迭 [ **BDC 方法詳細資料** ] 視窗中的節點，以定義參數、實例和篩選描述項。 使用 **BDC Explorer** 來定義型別描述項。

## <a name="bdc-explorer"></a>BDC 總管
 **BDC Explorer** 會顯示組成模型的元素。 若要開啟 **BDC Explorer**，請在功能表列上選擇 [ **View**  >  **Other Windows**  >  **BDC explorer**]。 若要流覽模型，請展開 [ **BDC Explorer**] 中的 [節點]。 每個節點都代表模型檔案的 XML 中的元素。

 當您選擇 **BDC Explorer** 中的節點時，您所選擇之每個節點的屬性都會出現在 [ **屬性** ] 視窗中。 其中許多屬性都對應至模型檔案中的屬性。 您可以使用 **BDC Explorer** 頂端的 [搜尋] 方塊來搜尋模型。

> [!NOTE]
> **BDC Explorer** 不會顯示識別碼、自訂屬性、當地語系化字串、關聯群組、動作、篩選描述項、動作控制項清單和預設參數值。

### <a name="define-type-descriptors"></a>定義類型描述元
 使用 **BDC Explorer** 來定義型別描述項。 BDC Explorer 可讓您定義一次型別描述項，然後在模型中的其他位置重複使用該型別描述元。 若要完成此動作，請複製類型描述元，並將其貼到任何其他參數或類型描述元。

> [!NOTE]
> 原始類型描述項的變更不會影響該類型描述元的複本。

 如需詳細資訊，請參閱 [如何：定義參數的類型描述](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)元。

## <a name="see-also"></a>另請參閱
- [如何：建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)
- [如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [如何：加入搜尋工具方法](../sharepoint/how-to-add-a-finder-method.md)
- [如何：新增特定搜尋工具方法](../sharepoint/how-to-add-a-specific-finder-method.md)
- [如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)
- [如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)
- [如何：加入更新程式方法](../sharepoint/how-to-add-an-updater-method.md)
- [建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)
- [逐步解說：使用商務資料在 SharePoint 中建立外部清單](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [將商務資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
- [建立商務資料連線模型](../sharepoint/creating-a-business-data-connectivity-model.md)
- [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)
