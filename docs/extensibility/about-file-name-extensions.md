---
title: "關於副檔名的檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8f504a70950ea9e808d50bd8b9bc7ef5dd92d699
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="about-file-name-extensions"></a>關於檔案名稱副檔名
當您註冊 VSPackage 的副檔名時，您將它與關聯的版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 這是重要如果多個版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]安裝在電腦上。  
  
 Vspackage 的檔案延伸模組都註冊在 HKEY_CLASSES_ROOT 索引鍵相關聯的程式設計識別項 (ProgID) 所指向的預設值。  
  
 .Vcproj 檔案延伸模組的註冊資訊的範例如下：  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 檔案與相關聯[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]必須具有版本設定的 ProgID，例如`VisualStudio.vcproj.8.0`允許維護檔案副檔名關聯的產品版本的產品-並存安裝。 版本特定 ProgID 也可讓您使用標準動詞命令，例如開啟、 編輯等等，而不需考慮的覆寫或遭到覆寫其他應用程式或新版[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
 在某些情況下，不應該變更副檔名相關聯的 ProgID。 例如，.htm 副檔名的 ProgID (progid = htmlfile) 是硬式編碼在某個作業系統中的小數位數，且廣泛已知且使用中關聯.htm 與.html 檔案。  
  
## <a name="see-also"></a>請參閱  
 [註冊檔案名稱擴充功能-並存部署](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [指定適用於副檔名的檔案處理常式](../extensibility/specifying-file-handlers-for-file-name-extensions.md)