---
title: 關於副檔名 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1146c7ed7bfc0d3f09d6c1848bf52345661bf0c7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54995030"
---
# <a name="about-file-name-extensions"></a>關於副檔名
當您註冊 VSPackage 的副檔名時，您將它產生關聯的版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 這是重要如果多個版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]安裝在電腦上。  
  
 下註冊 Vspackage 的檔案副檔名**HKEY_CLASSES_ROOT**索引鍵相關聯的程式設計識別項 (ProgID) 所指向的預設值。  
  
 下列範例示範的註冊資訊 *.vcproj*副檔名：  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 檔案與相關聯[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]必須有已建立版本的 ProgID，例如`VisualStudio.vcproj.8.0`。 建立版本的 ProgID，可讓維護產品版本之間的檔案副檔名關聯的產品來並行安裝。 版本特定 ProgID 也可讓您使用標準動詞命令，例如開啟、 編輯、 等等，而不用擔心的覆寫或遭到覆寫其他應用程式或新版[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
 在某些情況下，不應該變更副檔名相關聯的 ProgID。 比方說，如 ProgID *.htm*副檔名 (progid = htmlfile) 位於硬式編碼的幾個地方在作業系統中，而且廣泛已知且使用中關聯 *.htm*並 *.html*檔案。  
  
## <a name="see-also"></a>另請參閱  
 [註冊並排顯示部署的檔案名稱副檔名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [指定檔案名稱副檔名的檔案處理常式](../extensibility/specifying-file-handlers-for-file-name-extensions.md)