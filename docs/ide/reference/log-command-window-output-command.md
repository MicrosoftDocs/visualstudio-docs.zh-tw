---
title: 記錄命令視窗輸出命令 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57a1393c6db4da7b652490cbf9d352ad7b4455cd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="log-command-window-output-command"></a>記錄命令視窗輸出命令
將來自 [命令] 視窗的所有輸入和輸出複製到檔案中。  
  
## <a name="syntax"></a>語法  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 選擇性。 記錄檔的名稱。 根據預設，檔案會建立在使用者的設定檔資料夾中。 如果檔案名稱已經存在，就會將記錄附加至現有的檔案結尾。 如果未指定任何檔案，則會使用最近指定的檔案。 如果沒有先前的檔案存在，會建立預設記錄檔，稱為 cmdline.log。  
  
> [!TIP]
>  若要變更儲存記錄檔的位置，請輸入檔案的完整路徑，如果路徑包含任何空格則以引號括住。  
  
## <a name="switches"></a>參數  
 /on  
 選擇性。 開始在指定的檔案中記錄 [命令] 視窗，並將新資訊附加至檔案。  
  
 /off  
 選擇性。 停止 [命令] 視窗的記錄。  
  
 /overwrite  
 選擇性。 如果在 `filename` 引數指定的檔案符合現有檔案，即會覆寫該檔案。  
  
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
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)