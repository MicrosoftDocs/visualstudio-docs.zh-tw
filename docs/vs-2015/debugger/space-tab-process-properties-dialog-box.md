---
title: 空間索引標籤，處理序屬性對話方塊 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: de5df4c55feba8c9aaba0def7585029cc71426b5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945598"
---
# <a name="space-tab-process-properties-dialog-box"></a>處理序屬性對話方塊、空間索引標籤
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用**空間**檢查處理序的位址空間 索引標籤。 若要顯示[處理序屬性對話方塊](../debugger/process-properties-dialog-box.md)，焦點移至[處理序檢視](../debugger/processes-view.md)視窗。 在樹狀目錄中，選取任何處理序節點，然後選擇**屬性**從**檢視**功能表。  
  
 下列設定位於**空間** 索引標籤：  
  
|進入|描述|  
|-----------|-----------------|  
|[顯示標記空間]|使用此清單方塊選取的空間 （影像、 對應、 保留，或未指派） 類別。|  
|[Executable 位元組]|針對選取的分類中，所有使用此程序的位址空間的總和。 可執行檔的記憶體是指可以執行程式，但不是能讀取或寫入。|  
|[Exec-Read-Only 位元組]|針對選取的分類中，使用此程序所使用的唯讀屬性的使用中的所有位址空間的總和。 Exec 唯讀記憶體是指可以是執行，以及讀取。|  
|[Exec-Read-Write 位元組]|針對選取的分類中，使用此程序所使用的讀寫屬性的使用中的所有位址空間的總和。 Exec-讀取-寫入記憶體是可執行程式，以及讀取和修改。|  
|**Exec 寫入複製位元組**|針對選取的分類中，所有可執行程式，以及讀取 / 寫入的位址空間的總和。 需要處理序之間共用的記憶體時，會使用這種類型的保護。 如果共用的程序只會讀取記憶體，則它們會都使用相同的記憶體。 如果共用的處理序需要寫入權限，此記憶體的複本將會進行處理序。|  
|[No-Access 位元組]|針對選取的分類中，所有使用它時，防止處理程序的位址空間的總和。 如果寫入，就會產生存取違規或嘗試讀取。|  
|[Read-Only 位元組]|針對選取的分類中，所有的位址空間可以是執行，以及讀取的總和。|  
|[Read-Write 位元組]|針對選取的分類中，所有允許讀取和寫入的位址空間的總和。|  
|[Write-Copy 位元組]|選取的分類，所有的位址空間的總和，可讓記憶體共用進行讀取，但不是進行寫入。 當處理程序讀取記憶體時，他們可以共用相同的記憶體。 不過，當共用的程序想要讀取/寫入存取此共用的記憶體，記憶體的複本會進行寫入。|
