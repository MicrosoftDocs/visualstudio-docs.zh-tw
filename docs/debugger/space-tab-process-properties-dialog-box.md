---
title: 進程屬性對話方塊、空間索引標籤 |Microsoft Docs
description: 瞭解如何在偵錯工具中顯示 Spy + + 中的 [處理屬性] 對話方塊。 檢查 [空間] 索引標籤中可用的設定。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe168f34baf65b00eab59e94afb30e07dfe89b50
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149075"
---
# <a name="space-tab-process-properties-dialog-box"></a>處理序屬性對話方塊、空間索引標籤
使用 [ **空間** ] 索引標籤來檢查進程的位址空間。 若要顯示 [ [處理常式屬性] 對話方塊](../debugger/process-properties-dialog-box.md)，請將焦點移至 [ [進程] 視圖](../debugger/processes-view.md) 視窗。 選取樹狀結構中的任何進程節點，然後從 [ **View** ] 功能表選擇 [**屬性**]。

 [ **空間** ] 索引標籤上提供下列設定：

|進入|描述|
|-----------|-----------------|
|[顯示標記空間]|使用此清單方塊來選取空間 (影像、對應、保留或未指派) 的分類。|
|[Executable 位元組]|針對選取的類別，這是此進程使用的所有位址空間的總和。 可執行檔記憶體是可由程式執行，但可能無法讀取或寫入的記憶體。|
|[Exec-Read-Only 位元組]|針對選取的類別，這是使用此處理程式所使用之唯讀屬性的所有位址空間總和。 Exec-唯讀記憶體是可以執行並讀取的記憶體。|
|[Exec-Read-Write 位元組]|針對選取的類別，這是使用此處理程式所使用之讀寫屬性的所有位址空間總和。 Exec-讀寫記憶體是可由程式執行以及讀取和修改的記憶體。|
|**Exec-寫入複製位元組**|針對選取的類別，這是可由程式執行以及讀取和寫入的所有位址空間的總和。 當需要在進程間共用記憶體時，就會使用這種類型的保護。 如果共用進程唯讀取記憶體，則它們都會使用相同的記憶體。 如果共用進程需要寫入存取權，則會對此程式進行此記憶體的複本。|
|[No-Access 位元組]|針對選取的類別，這是防止進程使用它的所有位址空間的總和。 嘗試寫入或讀取時，就會產生存取違規。|
|[Read-Only 位元組]|針對選取的類別，這是可以執行及讀取的所有位址空間的總和。|
|**讀寫位元組**|針對選取的類別，這是允許讀取和寫入的所有位址空間的總和。|
|[Write-Copy 位元組]|針對選取的類別，這是所有位址空間的總和，可允許記憶體共用以供讀取，但無法寫入。 當進程讀取此記憶體時，它們可以共用相同的記憶體。 不過，當共用進程希望擁有此共用記憶體的讀取/寫入存取權時，就會建立該記憶體的複本以進行寫入。|