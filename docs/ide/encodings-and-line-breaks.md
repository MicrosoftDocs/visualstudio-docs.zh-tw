---
title: "編碼與分行符號 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 34c400c280096acb7e0ce272fa717cbc2f8f0d8a
ms.contentlocale: zh-tw
ms.lasthandoff: 05/24/2017

---
# <a name="encodings-and-line-breaks"></a>編碼與分行符號
在 Visual Studio 中，您可以使用 [檔案]/[進階儲存選項] 設定，判斷您要的分行符號字元類型。 您也可以變更具有相同設定之檔案的編碼。  
  
> [!NOTE]
>  如果您有特定類型的開發設定 (Visual Basic、F#、Web Development)，則在功能表上可能看不到 [進階儲存選項]。 若要變更設定 (例如 [一般])，請開啟 [工具]/[匯入和匯出設定]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
 在 Visual Studio 中，會將下列字元解譯為分行符號：  
  
-   CRLF：歸位字元 + 換行字元、Unicode 字元 000D + 000A  
  
-   LF：換行字元、Unicode 字元 000A  
  
-   NEL：下一行、Unicode 字元 0085  
  
-   LS：行分隔符號、Unicode 字元 2028  
  
-   PS：段落分隔符號、Unicode 字元 2029  
  
 從其他應用程式複製的文字會保留原始編碼和分行符號字元。 例如，當您從 [記事本] 中複製文字，並將它貼到 Visual Studio 中的文字檔，文字的設定會與它在 [記事本] 中的設定相同。  
  
 當您開啟的檔案包含不同的分行符號字元時，可能會看到一個對話方塊，詢問是否應該正規化不一致的分行符號字元以及要選擇哪一種分行符號類型。
