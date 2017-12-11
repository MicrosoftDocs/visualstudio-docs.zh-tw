---
title: "記錄命令視窗輸出命令 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 21450a0478bb7f2388cdde6b69f6fe661e9a055c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="log-command-window-output-command"></a>記錄命令視窗輸出命令
將來自 [命令] 視窗的所有輸入和輸出複製到檔案中。  
  
## <a name="syntax"></a>語法  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 選擇項。 記錄檔的名稱。 根據預設，檔案會建立在使用者的設定檔資料夾中。 如果檔案名稱已經存在，就會將記錄附加至現有的檔案結尾。 如果未指定任何檔案，則會使用最近指定的檔案。 如果沒有先前的檔案存在，會建立預設記錄檔，稱為 cmdline.log。  
  
> [!TIP]
>  若要變更儲存記錄檔的位置，請輸入檔案的完整路徑，如果路徑包含任何空格則以引號括住。  
  
## <a name="switches"></a>參數  
 /on  
 選擇項。 開始在指定的檔案中記錄 [命令] 視窗，並將新資訊附加至檔案。  
  
 /off  
 選擇項。 停止 [命令] 視窗的記錄。  
  
 /overwrite  
 選擇項。 如果在 `filename` 引數指定的檔案符合現有檔案，即會覆寫該檔案。  
  
## <a name="remarks"></a>備註  
 如果未指定任何檔案，預設會建立檔案 cmdline.log。 此命令的別名預設為 Log。  
  
## <a name="examples"></a>範例  
 這個範例會建立新的記錄檔 cmdlog，並開始命令記錄。  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 這個範例會停止記錄命令檔。  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 這個範例會繼續在先前使用的記錄檔中記錄命令。  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)