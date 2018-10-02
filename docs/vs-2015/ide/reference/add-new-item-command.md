---
title: 新增項目命令 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8f380a11440ed413871d2c80603148aa7cc77390
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496546"
---
# <a name="add-new-item-command"></a>加入新項目命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[加入新項目命令](https://docs.microsoft.com/visualstudio/ide/reference/add-new-item-command)。  
  
  
將新的方案項目，例如 .htm、.css、.txt 或框架組新增至目前的方案，並開啟它。  
  
## <a name="syntax"></a>語法  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 選擇性。 要新增至方案之項目的路徑和檔名。  
  
## <a name="switches"></a>參數  
 /t: `templatename`  
 選擇性。 指定要建立之檔案的類型。 如果未指定任何範本名稱，則預設會建立文字檔。  
  
 /t:`templatename` 引數語法會鏡像 [Add New Solution Item] (新增方案項目) 對話方塊中所找到的資訊。 您必須輸入後接檔案類型的完整分類，且使用反斜線 (`\`) 隔開分類名稱與檔案類型，並使用引號括住整個字串。  
  
 例如，若要建立新的文字檔，您將針對 /t:`templatename` 引數輸入下列項目。  
  
```  
/t:"General\Style Sheet"  
```  
  
 /e: `editorname`  
 選擇性。 將用來開啟檔案之編輯器的名稱。 如果指定此引數，但未提供編輯器名稱，則會出現 [開啟方式] 對話方塊。  
  
 /e:`editorname` 引數語法會使用出現在 [開啟方式] 對話方塊並使用引號括住的編輯器名稱。  
  
 例如，若要使用原始程式碼編輯器開啟樣式表，您將針對 /e:`editorname` 引數輸入下列項目。  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="example"></a>範例  
 此範例會將新的方案項目 MyHTMLpg 新增至目前方案。  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)



