---
title: "檔案中取代命令 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ccb81bffa6845e4e644294916a508820445da263
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="replace-in-files-command"></a>檔案中取代命令
使用在 [尋找和取代] 視窗 [檔案中取代] 索引標籤提供的選項子集，取代檔案中的文字。  
  
## <a name="syntax"></a>語法  
  
```  
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]  
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]  
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]  
```  
  
## <a name="arguments"></a>引數  
 `findwhat`  
 必要。 要比對的文字。  
  
 `replacewith`  
 必要。 要用來取代相符文字的文字。  
  
## <a name="switches"></a>參數  
 /all 或 /a  
 選擇項。 以取代文字來取代所有出現的搜尋文字。  
  
 /case 或 /c  
 選擇項。 只有當大寫和小寫字元完全符合 `findwhat` 引數中所指定的項目時，才會出現相符項目。  
  
 /ext: `extensions`  
 選擇項。 指定要搜尋之檔案的副檔名。  
  
 /keep 或 /k  
 選擇項。 指定所有修改過的檔案皆保持開啟。  
  
 /lookin: `searchpath`  
 選擇項。 要搜尋的目錄。 如果路徑包含空格，請將完整路徑用引號括住。  
  
 /options 或 /t  
 選擇項。 顯示目前的尋找選項設定清單，但不會執行搜尋。  
  
 /regex 或 /r  
 選擇項。 可將 `findwhat` 引數中預先定義的特殊字元作為標記法，以表示文字模式，而不是常值字元模式。 如需規則運算式字元的完整清單，請參閱[規則運算式](../../ide/using-regular-expressions-in-visual-studio.md)。  
  
 /reset 或 /e  
 選擇項。 將尋找選項還原為預設值，但不會執行搜尋。  
  
 /stop  
 選擇項。 中止目前正在進行中的搜尋作業。 若已指定 `/stop`，則取代會忽略所有其他引數。 例如，若要停止目前的取代，您要輸入下列項目︰  
  
```  
>Edit.ReplaceinFiles /stop  
```  
  
 /sub 或 /s  
 選擇項。 搜尋 /lookin:`searchpath` 引數所指定之目錄內的子資料夾。  
  
 /text2 或 /2  
 選擇性。 在 [尋找結果 2] 視窗中顯示取代結果。  
  
 /wild 或 /l  
 選擇項。 可將 `findwhat` 引數中預先定義的特殊字元作為標記法，以表示字元或字元序列。  
  
 /word 或 /w  
 選擇項。 只搜尋全字相符。  
  
## <a name="example"></a>範例  
 此範例會在 "my visual studio projects" 資料夾的所有 .cls 檔案中搜尋 `btnCancel`，並以 `btnReset` 取代它，在 [尋找結果 2] 視窗中顯示取代資訊。  
  
```  
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2  
```  
  
## <a name="see-also"></a>請參閱  
 [尋找和取代文字](../../ide/finding-and-replacing-text.md)   
 [檔案中取代](../../ide/replace-in-files.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)