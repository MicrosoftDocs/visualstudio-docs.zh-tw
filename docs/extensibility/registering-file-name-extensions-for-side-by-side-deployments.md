---
title: 註冊並行部署的檔案名副檔名 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6717625a44b48a25d293f68d01cd9fa3c7c24853
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701545"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>註冊並行部署的檔案名副檔名
對於並行環境中部署的 VSPackages,必須註冊檔案名副檔名,才能將檔案與的正確版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]相關聯 。 除非使用特定於版本的檔名副檔名,否則註冊使用戶能夠[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在相應的版本中打開專案和專案專案檔。

## <a name="in-this-section"></a>本節內容
- [關於檔案名副檔名](../extensibility/about-file-name-extensions.md)討論如何註冊檔名副檔名。

- [為檔案名副檔名指定檔案處理程式](../extensibility/specifying-file-handlers-for-file-name-extensions.md)提供有關如何註冊可以打開、編輯等特定檔名擴展名的應用程式的資訊。

- [註冊檔案名副檔名的謂詞](../extensibility/registering-verbs-for-file-name-extensions.md)討論如何註冊動詞。

- [管理並行檔案關聯](../extensibility/managing-side-by-side-file-associations.md)討論如何並行處理應呼叫 的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]特定版本的安裝來打開檔。

## <a name="related-sections"></a>相關章節
- [支援多個版本的視覺化工作室](../extensibility/supporting-multiple-versions-of-visual-studio.md)描述在開發和部署到最終使用者期間與[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]多個版本和 VSPackage 相關的問題。
