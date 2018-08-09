---
title: 註冊副檔名，並排顯示部署 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1aa553b5370f637f5a779bbdff432319ce3e0bf4
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638475"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>註冊並排顯示部署的檔案名稱副檔名
適用於並排顯示環境中部署的 Vspackage，您必須註冊檔案相關聯的正確版本的檔案名稱副檔名[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 除非您使用版本特定檔案的副檔名，註冊可讓使用者開啟您的專案和專案項目檔中的適當版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
 [關於副檔名](../extensibility/about-file-name-extensions.md)  
 討論如何註冊副檔名的檔案。  
  
 [指定檔案名稱副檔名的檔案處理常式](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 提供有關如何註冊應用程式，可以開啟、 編輯和等等，特定副檔名的資訊。  
  
 [註冊副檔名的動詞命令](../extensibility/registering-verbs-for-file-name-extensions.md)  
 討論如何註冊動詞命令。  
  
 [管理並排顯示檔案關聯](../extensibility/managing-side-by-side-file-associations.md)  
 討論如何處理在其中的並排顯示安裝特定版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]應該叫用它來開啟檔案。  
  
## <a name="related-sections"></a>相關章節  
 [支援多個版本的 Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 說明多個版本的相關問題[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和 VSPackage 開發及部署給使用者時。