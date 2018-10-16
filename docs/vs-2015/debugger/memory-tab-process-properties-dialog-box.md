---
title: 記憶體索引標籤，處理序屬性對話方塊 |Microsoft Docs
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
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 724e760c585f0e6423164e1a6bb28aefbf696c2f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245790"
---
# <a name="memory-tab-process-properties-dialog-box"></a>處理序屬性對話方塊、記憶體索引標籤
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用**記憶體** 索引標籤以顯示處理程序如何使用記憶體。 若要顯示[處理序屬性對話方塊](../debugger/process-properties-dialog-box.md)，焦點移至[處理序檢視](../debugger/processes-view.md)視窗。 在樹狀目錄中，選取任何處理序節點，然後選擇**屬性**從**檢視**功能表。  
  
 下列設定位於**記憶體** 索引標籤：  
  
|進入|描述|  
|-----------|-----------------|  
|**虛擬位元組**|處理序正在使用虛擬位址空間的目前大小 （以位元組為單位）。 使用虛擬位址空間不一定表示對應使用到磁碟或主記憶體分頁。 不過，虛擬空間是有限的而且使用太多可能會限制程序能夠載入程式庫。|  
|**尖峰虛擬位元組**|最大的虛擬位址空間的程序的位元組數已使用一次。|  
|**工作集**|最近處理程序中執行緒的記憶體分頁集。 如果電腦中的可用記憶體高於臨界值，即使未使用頁面會保留在處理程序的工作集中。 當可用記憶體低於臨界值時，頁面會刪減工作集中。 如果需要將其寫回工作集之前離開主記憶體。|  
|**尖峰工作集**|在此處理序在任何時間點的工作集的頁面數目上限。|  
|**分頁集區位元組**|目前處理序已配置的分頁集區的量。 分頁集區是系統記憶體區域，作業系統元件時，取得空間他們完成指定的工作。 分頁集區頁面可以分頁移出至分頁檔有持續一段時間未存取系統。|  
|**非分頁集區位元組**|目前的程序所配置的非分頁集區中的位元組數目。 非分頁集區是系統記憶體區域，取得空間的作業系統元件完成其指定的工作。 非分頁集區頁面無法移出分頁寫入分頁檔案。它們會處於主記憶體，只要已配置。|  
|**私用位元組**|目前的此程序已配置的位元組數目不能與其他處理序共用。|  
|**可用位元組**|此處理序的總未使用的虛擬位址空間。|  
|**保留的位元組**|保留供日後使用此程序的虛擬記憶體總數。|  
|**可用影像位元組**|未使用或保留此處理序內的映像的虛擬位址空間數量。|  
|**保留的影像位元組**|執行此處理序內的影像所保留的所有虛擬記憶體的總和。|



