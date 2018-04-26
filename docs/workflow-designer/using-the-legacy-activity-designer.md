---
title: 工作流程設計工具-使用舊版活動設計工具
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fdf7ae585697db19293362a31c5751d44c7421c5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="using-the-legacy-activity-designer"></a>使用舊版活動設計工具

本主題描述如何在舊版的 Windows 工作流程設計工具中使用活動設計工具。 .NET Framework 3.5 版或 WinFX 為目標時，請使用舊版設計工具。

活動設計工具可讓您建立自訂活動。

## <a name="creating-a-custom-activity"></a>建立自訂活動

依照下列步驟使用活動設計工具建立自訂活動：

1.  在**專案**功能表上，按一下 **新增活動**。

2.  選取**活動**或**活動 （程式碼分開置放）**範本。

    1.  使用**活動**範本來建立活動的活動定義和使用者程式碼，在相同的程式碼檔案中。

    2.  使用**活動 （程式碼分開置放）**範本來建立活動的活動定義表示成工作流程標記，且使用者程式碼在不同的程式碼檔案中。

3.  輸入活動名稱或保留預設名稱，然後按一下**新增**。

您也可以建立一組自訂活動，藉由建立新的專案類型的**Workflow Activity Library**。 如需這種專案類型的詳細資訊，請參閱[How to： 建立工作流程活動程式庫 （舊版）](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)。

## <a name="configuring-an-activity"></a>設定活動

活動設計工具為使用中時，可使用屬性瀏覽器設定下表所列的屬性。

|屬性|註解|
|--------------|--------------|
|**名稱**|活動名稱。|
|**基底類別**|衍生活動的基底類別。 預設基底類別是[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)。 在**屬性**視窗中，按一下 **基底類別**省略 **[…]** 選取中的另一個基底類別[瀏覽並選取.NET 類型對話方塊 （舊版）](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)。|
|**描述**|使用者定義的活動描述。|
|**已啟用**|設定為**True**依預設，若要啟用活動執行和驗證。 設定為**False**停用活動的執行與驗證。 如需活動執行和驗證資訊，請參閱[開發工作流程活動](http://go.microsoft.com/fwlink?LinkID=65024)。|

## <a name="adding-child-activities"></a>新增子活動

您可以將子活動從 [工具箱] 拖曳至您正在設計的活動。 接著，便可以使用屬性瀏覽器設定每一個子活動。

## <a name="see-also"></a>另請參閱

- [開發工作流程活動](http://go.microsoft.com/fwlink?LinkID=65024)
- [建立自訂活動](http://go.microsoft.com/fwlink?LinkID=65021)
- [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)
- [自訂活動範例](http://go.microsoft.com/fwlink?LinkID=65022)
- [如何：建立工作流程活動程式庫 (舊版)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)
- [使用舊版工作流程設計工具](../workflow-designer/using-the-legacy-workflow-designer.md)