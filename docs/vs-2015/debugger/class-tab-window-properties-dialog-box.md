---
title: 類別索引標籤，視窗屬性對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6eba6a12714c1b4f58ae9d6bb17f696c3c452411
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749334"
---
# <a name="class-tab-window-properties-dialog-box"></a>視窗屬性對話方塊、類別索引標籤
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用**類別**索引標籤，以顯示選取的視窗的類別上的資訊。 若要顯示[視窗中 [屬性] 對話方塊中](../debugger/window-properties-dialog-box.md)，焦點移至[Windows 檢視](../debugger/windows-view.md)視窗。 在樹狀目錄中，選取視窗的任何節點，然後選擇**屬性**從**檢視**功能表。  
  
 下列設定位於**類別** 索引標籤：  
  
|進入|描述|  
|-----------|-----------------|  
|**類別名稱**|此視窗類別名稱 （或序號）。|  
|**類別樣式**|類別樣式代碼的組合。|  
|**類別位元組**|此視窗類別相關聯的應用程式專屬資料。|  
|**類別元素**|類別所傳回的 atom **RegisterClass**呼叫。|  
|**執行個體控制代碼**|登錄類別的模組執行個體控制代碼。 執行個體控制代碼不是唯一的。|  
|**視窗位元組**|這個類別的每個視窗相關聯的額外位元組數目。 這些位元組的意義取決於應用程式。 展開以查看 DWORD 格式的位元組值的清單方塊。|  
|**視窗程序**|目前的位址**WndProc**適用於 windows 的這個類別的函式。 這不同於**視窗程序**上**一般**索引標籤上，如果視窗子類別化。|  
|**功能表名稱**|主功能表的這個類別 （如果有任何功能表 「 無 」） 的 windows 與相關聯的名稱。|  
|**圖示控制代碼**|這個類別 （如果有任何圖示 「 無 」） 的 windows 與相關聯的圖示控制代碼。|  
|**資料指標控制代碼**|這個類別 （如果沒有任何資料指標 「 無 」） 的 windows 與相關聯的游標的控制代碼。|  
|**背景筆刷**|此類別中，或其中一個預先定義 COLOR_ * 色彩繪製視窗背景 （如果沒有筆刷 「 無 」） 的 windows 與相關聯的背景筆刷的控制代碼。|



