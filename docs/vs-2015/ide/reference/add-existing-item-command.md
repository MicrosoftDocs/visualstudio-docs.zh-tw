---
title: 新增現有項目命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7686c4db4984188a4f8c4a52343f1386e9edd909
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54797833"
---
# <a name="add-existing-item-command"></a>加入現有項目命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
將現有檔案新增至目前的方案，並開啟它。  
  
## <a name="syntax"></a>語法  
  
```  
File.AddExistingItem filename [/e:editorname]  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 必要項。 要新增至目前方案之項目的完整路徑和檔案名稱 (含副檔名)。 如果檔案路徑或檔案名稱包含空格，請使用引號括住完整路徑。  
  
## <a name="switches"></a>參數  
 /e: `editorname`  
 選擇性。 將用來開啟檔案之編輯器的名稱。 如果指定此引數，但未提供編輯器名稱，則會出現 [開啟方式] 對話方塊。  
  
 /e:`editorname` 引數語法會使用出現在 [開啟方式] 對話方塊並使用引號括住的編輯器名稱。 例如，若要使用原始程式碼編輯器開啟樣式表，您將針對 /e:`editorname` 引數輸入下列項目。  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="remarks"></a>備註  
 自動完成會在您鍵入時嘗試找出正確的路徑和檔案名稱。  
  
## <a name="example"></a>範例  
 此範例會將 Form1.frm 檔案新增至目前方案。  
  
```  
>File.AddExistingItem "C:\public\solution files\Form1.frm"  
```  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
