---
title: HOW TO：新增和移除功能相依性 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 13fc731dcf5d96db569a969244b2375939afee62
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636966"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>HOW TO：新增和移除功能相依性
  您的 SharePoint 功能可能取決於其他功能的功能或資料。 在這些情況下，您可以針對您的功能將這些其他功能標示為相依性。 如此一來，可確保 SharePoint 伺服器，會啟動相依的功能，才能啟用您的功能。

## <a name="add-dependencies"></a>新增相依性
 您可以加入方案中的其他功能，做為相依性。 如此一來，您可以確保，安裝和啟用您的功能會在安裝前所需的功能。

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>在方案中的功能上新增相依性

1.  開啟功能設計工具中，展開**功能啟用相依性**節點，然後選擇**新增** 按鈕。

2.  在**新增的功能啟用相依性**對話方塊方塊中，選擇**方案中的功能上新增相依性**選項按鈕，選擇您想要新增為相依性，功能的標題，然後選擇**新增** 按鈕。

     您可以新增多個功能選擇多個項目時選擇**Ctrl**索引鍵。

## <a name="addi-custom-dependencies"></a>叫做自訂相依性
 您可以加入 SharePoint 伺服器上的已部署的功能，為相依性。 如此一來，SharePoint 啟用程序會檢查並確定您的功能會在安裝前，會啟動所有相依的功能。

#### <a name="to-add-a-dependency-by-the-feature-id"></a>若要新增的功能識別碼的相依性

1.  開啟功能設計工具中，展開**功能啟用相依性**節點，然後選擇**新增** 按鈕。

2.  在 **新增的功能啟用相依性**對話方塊方塊中，選擇**加入自訂相依性**選項按鈕。

3.  在 **功能識別碼**文字中，輸入您想要將標示為啟用相依性，然後選擇 功能 GUID**新增** 按鈕。

## <a name="edit-custom-dependencies"></a>編輯自訂相依性
 您可以編輯您先前新增的自訂相依性。 不過，相依的功能會在您的方案可以只會移除，無法編輯。

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>若要變更的相依性的方案中的功能

1.  開啟功能設計工具，然後展開**功能啟用相依性**節點。

2.  選擇您想要編輯，然後選擇功能的名稱**編輯** 按鈕。

3.  在 **編輯的自訂功能啟用相依性** 對話方塊中，變更標題、 功能識別碼或描述，然後選擇**送出** 按鈕。

## <a name="remove-dependencies"></a>移除相依性

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>若要在方案中移除功能相依性

1.  在功能設計工具中，依序展開**功能啟用相依性**節點，選擇您想要移除此項目，然後選擇功能名稱**移除** 按鈕。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)
- [如何：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [如何：新增和移除 SharePoint 功能的項目](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
