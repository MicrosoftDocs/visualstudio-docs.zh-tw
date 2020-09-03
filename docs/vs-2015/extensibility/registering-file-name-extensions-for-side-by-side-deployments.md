---
title: 註冊並存部署的副檔名 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 354b91dd1282df9726c1ee9c47f610b0dfdd9c1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163689"
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>註冊副檔名以進行並存部署
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

針對並存環境中部署的 Vspackage，您必須註冊副檔名，才能將檔案與正確的版本建立關聯 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 除非您使用版本特定的副檔名，否則註冊可讓使用者在適當的版本中開啟您的專案和專案專案檔 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
## <a name="in-this-section"></a>本節內容  
 [關於副檔名](../extensibility/about-file-name-extensions.md)  
 討論副檔名的註冊方式。  
  
 [指定適用於副檔名的檔案處理常式](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 提供有關如何註冊可以開啟、編輯等的應用程式，以及特定副檔名的相關資訊。  
  
 [註冊適用於副檔名的動詞命令](../extensibility/registering-verbs-for-file-name-extensions.md)  
 討論如何註冊動詞。  
  
 [管理並存的檔案關聯](../extensibility/managing-side-by-side-file-associations.md)  
 討論如何處理並存安裝，其中應叫用特定版本的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 來開啟檔案。  
  
## <a name="related-sections"></a>相關章節  
 [支援多個 Visual Studio 版本](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 說明在開發和部署給使用者期間的多個 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 和 VSPackage 版本的相關問題。
