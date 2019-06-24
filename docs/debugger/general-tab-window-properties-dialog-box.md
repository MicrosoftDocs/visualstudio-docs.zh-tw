---
title: 一般索引標籤、 視窗屬性對話方塊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5160c79e2c8dae474927e6af7ebdc9e371e9edc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849556"
---
# <a name="general-tab-window-properties-dialog-box"></a>視窗屬性對話方塊、一般索引標籤
使用**一般**索引標籤，以顯示選取的視窗的相關資訊。 若要顯示[視窗中 [屬性] 對話方塊中](../debugger/window-properties-dialog-box.md)，焦點移至[Windows 檢視](../debugger/windows-view.md)視窗。 在樹狀目錄中，選取視窗的任何節點，然後選擇**屬性**從**檢視**功能表。

 下列設定位於**一般** 索引標籤：

|進入|描述|
|-----------|-----------------|
|[視窗標題]|文字在視窗的標題或包含在一個視窗中，如果它是控制項的文字。|
|[視窗控制代碼]|此視窗的唯一識別碼。 視窗控制代碼數字會重複使用;它們可以識別視窗只會針對該視窗的存留期。|
|[視窗程序]|此視窗的視窗程序函式的虛擬位址。 這個欄位也會指出這個視窗是否為 Unicode 的視窗，以及它是否子類別。|
|[矩形]|視窗的周框。 此外，也會顯示矩形的大小。 單位為像素的螢幕座標。|
|[還原方框]|還原視窗的周框。 此外，也會顯示矩形的大小。 還原的方框不同矩形的視窗最大化或最小化時，才。 單位為像素的螢幕座標。|
|[用戶端方框]|視窗工作區指定的週框。 此外，也會顯示矩形的大小。 單位為像素為單位相對於左上角的視窗工作區。|
|[執行個體控制代碼]|應用程式的執行個體控制代碼。 執行個體控制代碼不是唯一的。|
|**控制項 ID 或功能表的控制代碼**|如果為子視窗所顯示的視窗，控制項 ID 會顯示標籤。 控制項 ID 是一個整數，識別這個子視窗的控制項 id。 如果顯示的視窗不是子視窗，則會顯示功能表控制代碼的標籤。 功能表控制代碼是功能表的一個整數，識別與這個視窗相關聯的控制代碼。|
|[使用者資料]|附加至這個視窗結構的應用程式專屬資料。|
|[視窗位元組]|此視窗相關聯的額外位元組數目。 這些位元組的意義取決於應用程式。 展開以查看 DWORD 格式的位元組值的清單方塊。|