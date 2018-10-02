---
title: 藉由修改 Isolated 的 Shell。Pkgundef 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3741fc9abdae6693670538c80288dfdefcefd84e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486802"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>藉由修改 Isolated 的 Shell。Pkgundef 檔案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新版本位於[修改隔離 Shell 所使用。Pkgundef 檔案](https://docs.microsoft.com/visualstudio/extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file)。  
  
您可以修改 isolated 的 shell 應用程式中排除指定的登錄項目.pkgundef 檔案。 通常，第一次的電腦，啟動應用程式的 Visual Studio shell 將複製現有的 Visual Studio 登錄項目到應用程式的根登錄機碼。 這包括任何參考目前已安裝的 Vspackage。  
  
 若要排除 isolated 的 shell 應用程式特定的登錄項目，新增至應用程式.pkgundef 檔案套件金鑰後面的項目。 如同.pkgdef 檔案，表示索引鍵和項目也就是為 [$RootKey$] 或 [$RootKey$\\*子機碼*] 和 「*項目*"=*值*，其中*子機碼*是影響，之子機碼*項目*是要移除的項目並*值*是`""`或`dword:00000000`。  
  
 若要排除的登錄機碼中的多個項目，只是列出金鑰一次，後面接著要排除的每個項目的行。  
  
 若要排除 isolated 的 shell 應用程式的整個登錄機碼，將金鑰新增至應用程式.pkgundef 檔案，但未指定該索引鍵的任何登錄項目。  
  
 您可以在.pkgundef 檔案中加入註解。 單行註解必須具有兩個斜線與前兩個字元。  
  
 例如，若要移除**連接到資料庫**並**連接到提供 r**上的命令**工具** 功能表中，行取消註解：  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 並新增一行：  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 應用程式的.pkgundef 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 功能的封裝 Guid](../extensibility/package-guids-of-visual-studio-features.md)   
 [自訂 Isolated Shell](../extensibility/customizing-the-isolated-shell.md)

