---
title: 如何： 搜尋處理序中處理序檢視 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c9cd618768268b5c0bc4e3e99fbffd4fd65e874
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715085"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>如何：在處理序檢視中搜尋處理序
您可以使用它的處理序識別碼或模組字串做為搜尋準則來搜尋特定處理序中處理序檢視。 您也可以指定搜尋的初始方向。 在對話方塊中的欄位會顯示選取的處理序的屬性，在處理序樹狀目錄中。

### <a name="to-search-for-a-process-in-processes-view"></a>搜尋處理序檢視中的處理序

1. 因此排列的視窗，Spy + + 和作用[處理序檢視](../debugger/processes-view.md)視窗會顯示。

2. 從**搜尋**功能表上，選擇**尋找處理序**

    [處理序搜尋對話方塊](../debugger/process-search-dialog-box.md)隨即開啟。

3. 輸入的處理序識別碼或模組字串做為搜尋準則。

4. 清除，您不想指定值的任何欄位。

   > [!TIP]
   >  若要尋找模組所擁有的所有處理程序，請清除**程序**方塊，然後輸入中的模組名稱**模組** 方塊中。 然後使用**尋找下一個**繼續搜尋處理序。

5. 選擇**向上**或是**向下**初始搜尋的方向。

6. 按一下 [確定 **Deploying Office Solutions**]。

   如果找到相符的處理程序，它會以醒目提示**處理序檢視**視窗。