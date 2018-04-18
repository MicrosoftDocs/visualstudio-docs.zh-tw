---
title: 一般索引標籤視窗屬性對話方塊、 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0186b03bd599a3644321b186dbd19c8d7338aca5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="general-tab-window-properties-dialog-box"></a>視窗屬性對話方塊、一般索引標籤
使用**一般**索引標籤，以顯示選取的視窗的相關資訊。 若要顯示[視窗屬性對話方塊](../debugger/window-properties-dialog-box.md)，焦點移至[視窗檢視](../debugger/windows-view.md)視窗。 在樹狀目錄中，選取視窗中的任何節點，然後選擇 **屬性**從**檢視**功能表。  
  
 下列設定都適用於**一般** 索引標籤：  
  
|進入|描述|  
|-----------|-----------------|  
|**視窗標題**|中視窗標題、 文字或包含在一個視窗中，如果它是控制項的文字。|  
|**視窗控制代碼**|此視窗的唯一識別碼。 視窗控制代碼數字會重複使用。這些識別視窗只會針對該視窗的存留期。|  
|**視窗程序**|此視窗的視窗程序函式的虛擬位址。 這個欄位也會指出這個視窗是否為 Unicode 視窗中，以及它是子類別化。|  
|**矩形**|視窗的週框。 矩形的大小也會顯示。 單位為像素為單位的螢幕座標。|  
|**還原的方框**|還原視窗之周框。 矩形的大小也會顯示。 最大化或最小化視窗時，只還原的方框將不同的矩形。 單位為像素為單位的螢幕座標。|  
|**用戶端矩形**|視窗工作區之周框。 矩形的大小也會顯示。 單位為像素為單位相對的視窗工作區的左上方。|  
|**執行個體控制代碼**|應用程式的執行個體控制代碼。 執行個體控制代碼不是唯一的。|  
|**控制項 ID 或功能表的控制代碼**|如果顯示的視窗是子視窗，控制項 ID 會顯示標籤。 控制項 ID 是整數，用以識別此子視窗的控制項 id。 如果顯示的視窗不是子視窗，功能表控制代碼會顯示標籤。 功能表的控制代碼會識別與此視窗相關聯的功能表的控制代碼的整數。|  
|**使用者資料**|附加至此視窗結構的應用程式特定資料。|  
|**視窗位元組**|此視窗相關聯的額外位元組數目。 這些位元組的意義取決於應用程式。 展開清單方塊，請參閱 DWORD 格式中的位元組值。|