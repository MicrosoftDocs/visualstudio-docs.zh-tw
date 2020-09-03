---
title: 視窗屬性對話方塊、類別索引標籤 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a7f81a100b2c2311444732434df0f5c5599742a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161605"
---
# <a name="class-tab-window-properties-dialog-box"></a>視窗屬性對話方塊、類別索引標籤
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 [ **類別** ] 索引標籤來顯示所選視窗之類別的資訊。 若要顯示 [ [視窗屬性] 對話方塊](../debugger/window-properties-dialog-box.md)，請將焦點移至 [ [Windows View](../debugger/windows-view.md) ] 視窗。 選取樹狀結構中的任何視窗節點，然後從 [ **View** ] 功能表選擇 [**屬性**]。  
  
 [ **類別** ] 索引標籤提供下列設定：  
  
|進入|描述|  
|-----------|-----------------|  
|**類別名稱**|此視窗類別的名稱 (或序數) 。|  
|[類別樣式]****|類別樣式程式碼的組合。|  
|[類別位元組]****|與此視窗類別相關聯的應用程式特定資料。|  
|[類別 Atom]****|**RegisterClass**呼叫所傳回之類別的 atom。|  
|[執行個體控制代碼]****|註冊類別之模組的實例控制碼。 實例控制碼不是唯一的。|  
|[視窗位元組]****|與這個類別的每個視窗相關聯的額外位元組數目。 這些位元組的意義是由應用程式所決定。 展開清單方塊以查看 DWORD 格式的位元組值。|  
|[視窗程序]****|這個類別之 windows 的 **WndProc** 函式的目前位址。 這與 [**一般**] 索引標籤上的**視窗進程**不同（如果視窗是子類別）。|  
|[功能表名稱]****|如果沒有功能表) ，與這個類別的視窗相關聯的主功能表名稱 ( [無]。|  
|[圖示控制代碼]****|如果沒有圖示) ，與這個類別的視窗相關聯之圖示的控制碼 ( 為 "none"。|  
|[資料指標控制代碼]****|如果沒有任何資料指標) ，與這個類別的視窗相關聯的資料指標的控制碼 ( 為 "none"。|  
|[背景筆刷]****|與這個類別的視窗相關聯的背景筆刷的控制碼，或其中一個預先定義的 COLOR_ * 色彩，用於繪製視窗背景 ( "none" （如果沒有筆刷) ）。|
