---
title: "註冊檔案名稱的副檔名來並行部署 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 457f9e5303c71d73467815b581c091dc239c1b63
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>註冊檔案名稱擴充功能-並存部署
並行的環境中部署的 Vspackage，您必須註冊檔案關聯的正確版本的檔案名稱副檔名[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 除非您使用版本特定檔案的副檔名，註冊可讓使用者開啟您的專案和專案項目檔中的適當版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
 [關於副檔名](../extensibility/about-file-name-extensions.md)  
 討論如何註冊副檔名的檔案。  
  
 [指定適用於副檔名的檔案處理常式](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 提供如何註冊應用程式，可以開啟、 編輯和等等，特定副檔名的相關資訊。  
  
 [註冊適用於副檔名的動詞命令](../extensibility/registering-verbs-for-file-name-extensions.md)  
 討論如何註冊動詞命令。  
  
 [管理並存的檔案關聯](../extensibility/managing-side-by-side-file-associations.md)  
 討論如何處理的並行安裝所在的特定版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]應該被叫用以開啟檔案。  
  
## <a name="related-sections"></a>相關章節  
 [支援多個 Visual Studio 版本](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 描述相關的多個版本問題[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和 VSPackage 在開發和部署給使用者。