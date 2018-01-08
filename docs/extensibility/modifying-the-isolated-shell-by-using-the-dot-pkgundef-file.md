---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file
title: "使用修改 Isolated 的 Shell。Pkgundef 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dfe0e4b39e96d98718ff98025add521a678699ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>使用修改 Isolated 的 Shell。Pkgundef 檔案
您可以修改.pkgundef 来排除的檔案指定的登錄項目從獨立的 shell 應用程式。 一般而言，第一次的電腦，啟動應用程式的 Visual Studio shell 將複製現有的 Visual Studio 登錄項目到應用程式的根登錄機碼。 這包括任何參考目前已安裝的 Vspackage。  
  
 若要排除特定的登錄項目從獨立的 shell 應用程式，新增至應用程式.pkgundef 檔案的套件金鑰後面的項目。 如同.pkgdef 檔案，代表索引鍵和項目也就是以 [$RootKey$] 或 [$RootKey$\\*子機碼*] 和"*項目*"=*值*，其中*子機碼*會影響，子機碼*項目*是要移除的項目和*值*是`""`或`dword:00000000`。  
  
 若要排除的登錄機碼中的多個項目，只列出索引鍵一次，後面接著要排除的每個項目的行。  
  
 若要排除 isolated 的 shell 應用程式的整個登錄機碼，將金鑰加入至應用程式.pkgundef 檔，但未指定該金鑰的任何登錄項目。  
  
 您可以將註解加入.pkgundef 檔案。 單行註解必須有兩個斜線做為前兩個字元。  
  
 例如，若要移除**連接至資料庫**和**連接到 Serve r**命令**工具** 功能表中，行取消註解：  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 然後，加入一行：  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 傳送應用程式的.pkgundef 檔案。  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 功能的封裝 Guid](../extensibility/package-guids-of-visual-studio-features.md)   
 [自訂 Isolated Shell](../extensibility/customizing-the-isolated-shell.md)