---
title: 如何：新增和移除功能相依性 |Microsoft Docs
description: 請參閱 Visual Studio 中的功能設計工具，以瞭解如何在 SharePoint 方案中新增和移除功能相依性。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ebec7f6b1f6d777ce7b3b914ac5c1d5629190fcc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923584"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>如何：新增和移除功能相依性
  您的 SharePoint 功能可能相依于功能或資料的其他功能。 在這些情況下，您可以將這些其他功能標示為功能的相依性。 如此一來，SharePoint 伺服器便可確保在啟用功能之前，會先啟用相依功能。

## <a name="add-dependencies"></a>新增相依性
 您可以將解決方案中的其他功能新增為相依性。 如此一來，您可以在安裝功能之前，確定已安裝並啟用必要的功能。

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>若要在方案中新增功能的相依性

1. 開啟 [功能設計工具]，展開 [ **功能啟用** 相依性] 節點，然後選擇 [ **加入** ] 按鈕。

2. 在 [ **加入功能啟用** 相依性] 對話方塊中，選擇 [在 **方案中新增功能** 的相依性] 選項按鈕，選擇您想要新增為相依性的功能標題，然後選擇 [ **加入** ] 按鈕。

     您可以選擇多個標題，同時選擇 **Ctrl** 鍵，以新增多項功能。

## <a name="addi-custom-dependencies"></a>Addi 自訂相依性
 您可以加入已部署在 SharePoint 伺服器上的功能做為相依性。 如此一來，SharePoint 啟用程式就會檢查，以確定所有相依的功能在安裝您的功能之前都已啟動。

#### <a name="to-add-a-dependency-by-the-feature-id"></a>依功能識別碼新增相依性

1. 開啟 [功能設計工具]，展開 [ **功能啟用** 相依性] 節點，然後選擇 [ **加入** ] 按鈕。

2. 在 [ **加入功能啟用** 相依性] 對話方塊中，選擇 [ **加入自訂** 相依性] 按鈕。

3. 在 [ **功能識別碼** ] 文字方塊中，輸入您要標示為啟用相依性之功能的 GUID，然後選擇 [ **加入** ] 按鈕。

## <a name="edit-custom-dependencies"></a>編輯自訂相依性
 您可以編輯您先前新增的自訂相依性。 不過，您方案中的相依功能只能移除，而不會進行編輯。

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>變更解決方案中某項功能的相依性

1. 開啟 [功能設計工具]，然後展開 [ **功能啟用** 相依性] 節點。

2. 選擇您要編輯的功能名稱，然後選擇 [ **編輯** ] 按鈕。

3. 在 [ **編輯自訂功能啟用** 相依性] 對話方塊中，變更 [標題]、[功能識別碼] 或 [描述]，然後選擇 [ **提交** ] 按鈕。

## <a name="remove-dependencies"></a>移除相依性

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>移除方案中某項功能的相依性

1. 在 [功能設計工具] 中，展開 [ **功能啟用** 相依性] 節點，選擇您想要移除之功能的名稱，然後選擇 [ **移除** ] 按鈕。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)
- [如何：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [如何：新增和移除 SharePoint 功能的專案](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
