---
title: 使用舊版活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 534af8da414cb3b9cc0dd786f7b79abe00e2ed66
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606892"
---
# <a name="using-the-legacy-activity-designer"></a>使用舊版活動設計工具
本主題描述如何在舊版 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 中使用活動設計工具。 當以 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 或 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 為目標時，請使用舊版設計工具。

 活動設計工具可讓您建立自訂活動。

## <a name="creating-a-custom-activity"></a>建立自訂活動
 依照下列步驟使用活動設計工具建立自訂活動：

1. 在 [**專案**] 功能表上，按一下 [**加入活動**]。

2. 選取 [**活動**] 或 [**活動（使用程式碼分隔）** ] 範本。

   1. 使用**活動**範本，以相同程式碼檔案中的活動定義和使用者程式碼來建立活動。

   2. 使用**活動（使用程式碼分隔）** 範本來建立活動，其中活動定義會以工作流程標記和使用者程式碼在不同的程式碼檔案中表示。

3. 輸入活動名稱或保留預設名稱，然後按一下 [**新增**]。

   您也可以建立**工作流程活動程式庫**類型的新專案，以建立一組自訂活動。 如需此專案類型的詳細資訊，請參閱 [How to：建立工作流程活動程式庫（舊版） ](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)。

## <a name="configuring-an-activity"></a>設定活動
 活動設計工具為使用中時，可使用屬性瀏覽器設定下表所列的屬性。

|屬性|註解|
|--------------|--------------|
|**名稱**|活動名稱。|
|**基類**|衍生活動的基底類別。 預設基類為[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)。 在 [**屬性**] 視窗中，按一下 [**基類**省略號 **[...]]** ，在 [[流覽並選取 .net 類型] 對話方塊（舊版）](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)中選取另一個基類。|
|**描述**|使用者定義的活動描述。|
|**已啟用**|預設設定為**True**以啟用活動執行和驗證。 設定為**False**可停用活動執行和驗證。 如需活動執行和驗證的相關資訊，請參閱[開發工作流程活動](http://go.microsoft.com/fwlink?LinkID=65024)。|

## <a name="adding-child-activities"></a>新增子活動
 您可以將子活動從 [工具箱] 拖曳至您正在設計的活動。 接著，便可以使用屬性瀏覽器設定每一個子活動。

## <a name="see-also"></a>另請參閱
 [開發工作流程活動](http://go.microsoft.com/fwlink?LinkID=65024)[建立自訂活動](http://go.microsoft.com/fwlink?LinkID=65021)的[舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)[自訂活動範例](http://go.microsoft.com/fwlink?LinkID=65022)[How 至：[使用舊版工作流程設計工具來](../workflow-designer/using-the-legacy-workflow-designer.md)建立工作流程活動程式庫（舊版） ](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)