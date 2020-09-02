---
title: 使用來修改隔離式 Shell。.Pkgundef 檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eab02fe900e96ba37c63faae535974788f99ba78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538382"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>使用 .Pkgundef 檔案修改 Isolated Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以修改 .pkgundef 檔案，從隔離的 shell 應用程式中排除指定的登錄專案。 一般來說，第一次在電腦上啟動應用程式時，Visual Studio shell 會將現有的 Visual Studio 登錄專案複製到應用程式的根登錄機碼。 這包括任何對目前安裝之 Vspackage 的參考。  
  
 若要從隔離的 shell 應用程式中排除特定的登錄專案，請將封裝索引鍵後面接著專案加入 .pkgundef 檔案。 金鑰和專案的表示方式就像 .pkgdef 檔一樣。也就是說，as [$RootKey $] 或 [$RootKey $ 子機碼 \\ * *] 和 "*entry*" =*value*，其中子機碼是所要影響的子機碼， *entry*是要移除的專案，而*值*則是*subkey* `""` 或 `dword:00000000` 。  
  
 若要從登錄機碼中排除多個專案，只需列出機碼一次，然後在每個要排除的專案中加入一行。  
  
 若要從隔離的 shell 應用程式中排除整個登錄機碼，請將金鑰新增至 .pkgundef 檔案，但不要指定該金鑰的任何登錄專案。  
  
 您可以將批註新增至 .pkgundef 檔案。 單行批註必須有兩個斜線作為前兩個字元。  
  
 例如，若要在 [**工具**] 功能表上移除 [**連接至資料庫**並**連接至服務 r**命令]，您可以取消批註這一行：  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 然後新增該行：  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 應用程式的 .pkgundef 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 功能的套件 Guid](../extensibility/package-guids-of-visual-studio-features.md)   
 [自訂 Isolated Shell](../extensibility/customizing-the-isolated-shell.md)
