---
title: 關於副檔名 |Microsoft Docs
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
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b8a299d7b2470b16761e4a418e0717a91c2929e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499602"
---
# <a name="about-file-name-extensions"></a>關於副檔名
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[有關的檔案名稱副檔名](https://docs.microsoft.com/visualstudio/extensibility/about-file-name-extensions)。  
  
當您註冊 VSPackage 的副檔名時，您將它產生關聯的版本[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 這是重要如果多個版本[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]安裝在電腦上。  
  
 預設值的相關聯的程式設計識別項 (ProgID) 所指向的 HKEY_CLASSES_ROOT 機碼下註冊 Vspackage 的檔案副檔名。  
  
 .Vcproj 檔案延伸模組的註冊資訊的範例如下：  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 檔案與相關聯[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]必須有已建立版本的 ProgID，例如`VisualStudio.vcproj.8.0`，以便維護產品版本之間的檔案副檔名關聯的產品來並行安裝。 版本特定 ProgID 也可讓您使用標準動詞命令，例如開啟、 編輯、 等等，而不用擔心的覆寫或遭到覆寫其他應用程式或新版[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
 在某些情況下，不應該變更副檔名相關聯的 ProgID。 比方說，.htm 副檔名的 ProgID (progid = htmlfile) 設定為固定值中的幾個地方在作業系統中，而且廣泛已知且使用中關聯的.htm 與.html 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [並排顯示部署註冊副檔名的檔案](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [指定適用於副檔名的檔案處理常式](../extensibility/specifying-file-handlers-for-file-name-extensions.md)

