---
title: "產生類別或類型 - 程式碼產生 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: ebc361fe-d9b1-4c7a-ae28-5e71b5775460
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 87ef385a7e9edf9f975eb579bfab292039d60fa2
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-class-or-type-in-c"></a>使用 C# 來產生類別或類型 #
**功能：**讓您立即產生類別或類型的程式碼。 

**時機：** 您引進新的類別或類型，並想要自動正確地宣告它。  

**原因：**您可以在使用類別或類型之前先宣告它，不過，此功能將可自動產生類別或類型。 

**做法：**

1. 將游標放在有紅色曲線的行上，該曲線代表您使用尚未存在的類別。

   ![醒目標示的程式碼](media/class-highlight-cs.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取其中一個選項。
   * **滑鼠**
     * 按一下滑鼠右鍵並選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取其中一個選項。
     * 將游標暫留在紅色曲線上，然後按一下顯示的 ![燈泡](media/bulb-cs.png) 圖示。
     * 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在含有紅色曲線的行上，此圖示就會出現在左邊界上。

   ![「產生類別」預覽](media/class-preview-cs.png)

   選取 | 描述
   --- | ---
   在新檔案中產生類別 '*TypeName*' | 在名為 *TypeName*.cs/.vb 的檔案中建立名為 *TypeName* 的類別
   產生類別 '*TypeName*' | 在目前的檔案中建立名為 *TypeName* 的類別。
   產生巢狀類別 '*TypeName*' | 在目前的類別內建立名為 *TypeName* 的類別。
   產生新類型... | 使用您指定的所有屬性來建立新的類別或結構。

   >[!TIP]
   >請使用位於預覽視窗底部的 [[預覽變更](../../ide/preview-changes.md)] 連結，以在進行選取之前先查看將進行的所有變更。

1. 如果您選取 [產生新的類型] 項目，將會顯示可讓您執行一些額外動作的快顯對話方塊。

   ![產生類型](media/class-newtype-cs.png)

   選取 | 描述
   --- | ---
   存取 | 將類型設定為擁有 [預設]內部 或 [公用] 存取權。
   類型 | 這可以設定為 [類別] 或 [結構]。
   名稱 | 此名稱無法變更且將是您已經輸入的名稱。
   專案 | 如果您的方案中有多個專案，則您可以選擇要將類別/結構放在哪個專案中。
   檔案名稱 | 您可以建立新檔案，或是將類型新增至現有的檔案。

1. 系統將會使用從類別/結構使用方式推斷的建構函式來自動建立類別/結構。

   ![「產生類別」結果](media/class-result-cs.png)

## <a name="see-also"></a>另請參閱

[程式碼產生](../code-generation-in-visual-studio.md)  
[預覽變更](../../ide/preview-changes.md)