---
title: 索引標籤、所有語言、文字編輯器、選項 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 940cca6b25ffc04fc017ef8def6dbace7ec35ef9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213319"
---
# <a name="options-text-editor-all-languages-tabs"></a>索引標籤、所有語言、文字編輯器、選項
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
編輯樣式表時，這個對話方塊可讓您變更程式碼編輯器的預設行為。 這些設定也適用於以程式碼編輯器為基礎的其他編輯器，例如 HTML 設計工具的來源檢視。 若要顯示這些選項，請從 [工具] 功能表選取 [選項]。 在 [文字編輯器] 資料夾內，展開 [所有語言] 子資料夾，然後選擇 [定位點]。  
  
> [!CAUTION]
>  此頁面會設定所有開發語言的預設選項。 請記住，重設此對話方塊中的選項，會將所有語言中的 [定位點] 選項重設為此處所選的選項。 若只要變更單一語言的文字編輯器選項，請展開該語言的子資料夾，然後選取其選項頁面。  
  
 如果在特定程式設計語言的 [定位點] 頁面上選取不同的設定，則針對不同的 [縮排] 選項會顯示「個別文字格式的縮排設定彼此衝突」訊息，並且針對不同的 [定位點] 選項會顯示「個別文字格式的定位點設定彼此衝突」訊息。 例如，如果針對 Visual Basic 選取了 [智慧縮排] 選項，但針對 Visual C++ 選取 [區塊縮排]。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="indenting"></a>縮排  
 無  
 選取時，新行不會縮排。 插入點會放在新行的第一欄中。  
  
 區塊  
 選取時，新行會自動縮排。 插入點會放在與前一行相同的起始點。  
  
 智慧型  
 選取時，新行的位置會符合程式碼內容，依據其他程式碼格式設定，以及您開發語言的 IntelliSense 慣例。 此選項不適用於所有開發語言。  
  
 例如，左大括弧 ( { ) 和右大括弧 ( } ) 之間的行，可能會自動從對齊的大括弧位置縮排一個額外的定位停駐點。  
  
## <a name="tabs"></a>定位點  
 定位點大小  
 設定定位停駐點之間的距離 (以空格為單位)。 預設值為四個空格。  
  
 縮排大小  
 設定自動縮排的大小 (以空格為單位)。 預設值為四個空格。 插入定位字元、空格字元或兩者，以填滿指定的大小。  
  
 插入空格  
 選取時，縮排作業只會插入空格字元，而非定位字元。 例如，如果 [縮排大小] 設為 5，每次您按下 TAB 鍵，或按一下 [格式] 工具列上的 [增加縮排] 按鈕時，就會插入五個空格字元。  
  
 保留定位點  
 選取時，縮排作業會盡可能插入越多的定位字元。 每個定位字元都會以指定的 [定位點大小] 填入空格數。 如果 [縮排大小] 不是 [定位點大小] 的偶數倍數，就會加入空格字元填滿其間的差距。  
  
## <a name="see-also"></a>另請參閱  
 [選項、文字編輯器、所有語言](../../ide/reference/options-text-editor-all-languages.md)   
 [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)



