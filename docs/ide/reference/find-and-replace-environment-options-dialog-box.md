---
title: 選項對話方塊、環境、尋找和取代
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.FindReplace
- VS.ToolsOptionsPages.Environment.FindandReplace
helpviewer_keywords:
- Find and Replace, Options dialog box
- Find and Replace, customizing
ms.assetid: f804d6d5-6309-46e4-8294-b83e880b5ec9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ef53be4d3894dd1d22a3afbde9dbf631b472aa2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75569565"
---
# <a name="find-and-replace-environment-options-dialog-box"></a>選項對話方塊、環境、尋找和取代

使用 [選項]**** 對話方塊的這個頁面，即可控制訊息方塊以及尋找和取代作業的其他層面。 從 [工具]**** 功能表中按一下 [選項]****，並展開 [環境]****，然後按一下 [尋找和取代]****，即可存取此對話方塊。 如果此頁面未出現在清單中，請在 [選項]**** 對話方塊中選取 [顯示所有設定]****。

## <a name="uielement-list"></a>UIElement 清單

**顯示告知性訊息**

選取此選項，可顯示所有具有 [永遠顯示這個訊息]**** 選項的 [尋找和取代] 告知性訊息。 例如，如果您選擇不要顯示「尋找已到達搜尋起點」訊息，則選取此選項會導致這則告知性訊息在您使用 [尋找和取代] 時再次出現。

如果您不想查看任何 [尋找和取代] 告知性訊息，請清除此選項。

當您已經清除部分而非全部 [尋找和取代]**** 告知性訊息的 [永遠顯示這個訊息]**** 選項時，會填滿但未選取 [顯示告知性訊息]**** 核取方塊。 若要還原所有選擇性 [尋找和取代]**** 訊息，請清除此選項，然後再次選取它。

> [!NOTE]
> 此選項不會影響任何未顯示 [永遠顯示這個訊息]**** 選項的 [尋找和取代]**** 告知性訊息。

**顯示警告訊息**

選取此選項，可顯示所有具有 [永遠顯示這個訊息]**** 選項的警告性 [尋找和取代] 告知性訊息。 例如，如果您選擇不顯示 [全部取代]**** 警告訊息，而這則警告訊息是在嘗試於目前未開啟進行編輯的檔案中進行取代時顯示，選取此選項會在您嘗試進行全部取代時再次出現這則警告訊息。

如果您不想查看任何 [尋找和取代] 警告性訊息，請清除此選項。

當您已經清除部分而非全部 [尋找和取代]**** 警告訊息的 [永遠顯示這個訊息]**** 選項時，會填滿但未選取 [顯示警告訊息]**** 核取方塊。 若要還原所有選擇性 [尋找和取代]**** 訊息，請清除此選項，然後再次選取它。

> [!NOTE]
> 此選項不會影響任何未顯示 [永遠顯示這個訊息]**** 選項的 [尋找和取代]**** 警告訊息。

**用編輯器的文字自動填入 [尋找目標]**

選取此選項，可在您從 [編輯]**** 功能表中選取 [尋找和取代]**** 視窗的任何檢視時，將目前編輯器插入點任一端的文字貼入 [尋找目標]**** 欄位。 清除此選項，可使用前一個搜尋的最後一個搜尋模式作為 [尋找目標]**** 字串。

## <a name="see-also"></a>另請參閱

- [尋找和取代文字](../../ide/finding-and-replacing-text.md)
