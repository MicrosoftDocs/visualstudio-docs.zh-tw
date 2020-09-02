---
title: 視窗屬性對話方塊、一般索引標籤 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b8733ef63a60baa1b268c42c8780cdf80f2674b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159953"
---
# <a name="general-tab-window-properties-dialog-box"></a>視窗屬性對話方塊、一般索引標籤
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用 [ **一般** ] 索引標籤來顯示所選視窗的相關資訊。 若要顯示 [ [視窗屬性] 對話方塊](../debugger/window-properties-dialog-box.md)，請將焦點移至 [ [Windows View](../debugger/windows-view.md) ] 視窗。 選取樹狀結構中的任何視窗節點，然後從 [ **View** ] 功能表選擇 [**屬性**]。  
  
 [ **一般** ] 索引標籤提供下列設定：  
  
|進入|描述|  
|-----------|-----------------|  
|[視窗標題]****|視窗標題中的文字，或視窗中包含的文字（如果它是控制項的話）。|  
|**視窗控制代碼**|此視窗的唯一識別碼。 視窗控制碼號碼會重複使用;他們只會在該視窗的存留期內找出一個視窗。|  
|[視窗程序]****|此視窗的視窗程式函式的虛擬位址。 此欄位也會指出此視窗是否為 Unicode 視窗，以及是否為子類別。|  
|**矩形**|視窗的周框。 矩形的大小也會顯示。 單位是螢幕座標的圖元。|  
|[還原方框]****|已還原之視窗的周框。 矩形的大小也會顯示。 只有當視窗最大化或最小化時，還原的矩形才會與矩形不同。 單位是螢幕座標的圖元。|  
|[用戶端方框]****|視窗工作區的周框。 矩形的大小也會顯示。 單位是相對於視窗用戶端區域左上角的圖元。|  
|[執行個體控制代碼]****|應用程式的實例控制碼。 實例控制碼不是唯一的。|  
|**控制項識別碼或功能表控制碼**|如果要顯示的視窗是子視窗，則會顯示控制項識別碼標籤。 控制項識別碼是識別此子視窗的控制項識別碼的整數。 如果顯示的視窗不是子視窗，則會顯示功能表控點標籤。 功能表控點是一個整數，用來識別與此視窗相關聯之功能表的控制碼。|  
|**使用者資料**|附加至此視窗結構的應用程式特定資料。|  
|[視窗位元組]****|與此視窗相關聯的額外位元組數目。 這些位元組的意義是由應用程式所決定。 展開清單方塊以查看 DWORD 格式的位元組值。|
