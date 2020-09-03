---
title: 進程屬性對話方塊、記憶體索引標籤 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b70c5a982da866cbeb9e9907859ad4d270d79bd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203298"
---
# <a name="memory-tab-process-properties-dialog-box"></a>處理序屬性對話方塊、記憶體索引標籤
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用 [ **記憶體** ] 索引標籤可顯示進程如何使用記憶體。 若要顯示 [ [處理常式屬性] 對話方塊](../debugger/process-properties-dialog-box.md)，請將焦點移至 [ [進程] 視圖](../debugger/processes-view.md) 視窗。 選取樹狀結構中的任何進程節點，然後從 [ **View** ] 功能表選擇 [**屬性**]。  
  
 您可以在 [ **記憶體** ] 索引標籤上使用下列設定：  
  
|進入|描述|  
|-----------|-----------------|  
|**虛擬位元組**|目前的大小 (進程正在使用的虛擬位址空間) 位元組數。 使用虛擬位址空間時，不一定表示對應使用的是磁片或主儲存體頁面。 不過，虛擬空間是有限的，而且使用太多可能會限制進程載入程式庫的能力。|  
|**尖峰虛擬位元組**|進程已在任何一次使用之虛擬位址空間的最大位元組數目。|  
|**工作集**|進程中的執行緒最近接觸過的記憶體頁面集。 如果電腦中的可用記憶體大於閾值，即使是未使用到的記憶體頁也會保留在處理序的工作集中。 當可用記憶體低於閾值時，就會從工作集修剪頁面。 如果需要的話，它們會在離開主儲存體之前，以虛錯誤的的順序傳回工作集。|  
|**尖峰工作集**|在任何時間點，此進程之工作集內的最大頁面數目。|  
|**分頁集區位元組**|進程已配置的目前分頁集區數量。 分頁集區是系統記憶體區域，其中作業系統元件會在完成其所需的工作時取得空間。 如果系統未在持續時間記憶體取分頁檔案，分頁集區頁面可以分頁至分頁檔。|  
|**非分頁集區位元組**|進程所配置的非分頁集區中目前的位元組數目。 非分頁集區是系統記憶體區域，可讓作業系統元件在完成其所需的工作時取得空間。 非分頁集區頁面無法分頁至分頁檔案;只要配置，它們就會保留在主儲存體中。|  
|**私用位元組**|此處理程式配置的目前位元組數目無法與其他進程共用。|  
|**可用位元組**|此進程未使用的虛擬位址空間總數。|  
|**保留的位元組**|保留給此進程未來使用的虛擬記憶體總數量。|  
|**可用映像位元組**|此進程中未使用或由影像保留的虛擬位址空間數量。|  
|**保留的映像位元組**|在此程式中執行的映射所保留的所有虛擬記憶體總和。|
