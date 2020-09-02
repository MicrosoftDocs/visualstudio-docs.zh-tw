---
title: 關於副檔名 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 866a30279ca2c79f4a490a040f76bc3a86c6a6e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148040"
---
# <a name="about-file-name-extensions"></a>關於副檔名
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您註冊 VSPackage 的副檔名時，會將它與的版本建立關聯 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 如果電腦上安裝了一個以上的版本，這就很重要 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
 Vspackage 的副檔名是在 HKEY_CLASSES_ROOT 機碼下註冊，其預設值會指向 (ProgID) 的相關聯程式設計識別碼。  
  
 以下是 vcproj 副檔名的註冊資訊範例：  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 與相關聯的檔案 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 必須具有已建立版本的 ProgID （例如 `VisualStudio.vcproj.8.0` ），才能讓產品並存安裝，以維護產品版本之間的副檔名關聯。 版本特定的 ProgID 也可讓您使用標準動詞，例如開啟、編輯等，而不需要考慮其他應用程式或版本的覆寫或覆寫 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
 在某些情況下，與副檔名相關聯的 ProgID 不應變更。 例如，.htm 副檔名 (progid = htmlfile) 的 ProgID 是硬式編碼在作業系統的許多地方，而且很著名並用來與 .htm 和 .html 檔案關聯。  
  
## <a name="see-also"></a>另請參閱  
 [註冊並存部署的副檔名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [指定適用於副檔名的檔案處理常式](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
