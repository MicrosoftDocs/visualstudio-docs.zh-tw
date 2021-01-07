---
title: 進程屬性對話方塊、分頁檔索引標籤 |Microsoft Docs
description: 使用流程屬性的 [分頁檔] 索引標籤，檢查進程的分頁檔案。 本文描述可用的設定。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47f4a2e9215cb2e98fdfefecdf978cb4a442ad84
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975052"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>處理序屬性對話方塊、分頁檔索引標籤
您可以使用 [ **分頁檔** ] 索引標籤來檢查進程的分頁檔案。 若要顯示 [ [處理常式屬性] 對話方塊](../debugger/process-properties-dialog-box.md)，請將焦點移至 [ [進程] 視圖](../debugger/processes-view.md) 視窗。 選取樹狀結構中的任何進程節點，然後從 [ **View** ] 功能表選擇 [**屬性**]。

 [ **分頁檔** ] 索引標籤提供下列設定：

|進入|描述|
|-----------|-----------------|
|**分頁檔位元組**|此進程在分頁檔中使用的目前頁面數目。 分頁檔案會儲存進程所使用但不包含在其他檔案中的資料頁面。 分頁檔案是由所有進程使用，而且分頁檔案中缺少空間，可能會在其他進程正在執行時發生錯誤。|
|**尖峰分頁檔位元組**|此進程在分頁檔案中使用的最大頁面數目。|
|**分頁錯誤**|此處理程式中執行之執行緒的分頁錯誤數目。 當執行緒所參照照的虛擬記憶體分頁不在它的工作集主記憶體中時，就會發生分頁錯誤。 如此一來，如果頁面位於待命清單上，而且已經在主儲存體中，或與頁面共用的另一個進程正在使用該頁面，就不會從磁片取出該頁面。|