---
title: 註冊並存 Ide 的副檔名
description: 瞭解如何註冊並存部署的副檔名，讓使用者能夠在適當版本的 Visual Studio 中開啟檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a457a3848917eff3d3722a8e72f0b0b720c0b43b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836991"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>註冊並存部署的副檔名
針對並存環境中部署的 Vspackage，您必須註冊副檔名，才能將檔案與正確的版本建立關聯 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 除非您使用版本特定的副檔名，否則註冊可讓使用者在適當的版本中開啟您的專案和專案專案檔 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

## <a name="in-this-section"></a>本節內容
- [關於](../extensibility/about-file-name-extensions.md) 副檔名討論副檔名的註冊方式。

- [指定副檔名的檔案處理常式](../extensibility/specifying-file-handlers-for-file-name-extensions.md) 提供有關如何註冊可以開啟、編輯等的應用程式，以及特定副檔名的相關資訊。

- [註冊副檔名的動詞](../extensibility/registering-verbs-for-file-name-extensions.md) 討論如何註冊動詞。

- [管理並存檔案關聯](../extensibility/managing-side-by-side-file-associations.md) 討論如何處理並存安裝，其中應叫用特定版本的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 來開啟檔案。

## <a name="related-sections"></a>相關章節
- [支援 Visual Studio 的多個版本](../extensibility/supporting-multiple-versions-of-visual-studio.md) 描述 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 在開發和部署至使用者時，與多個版本和 VSPackage 相關的問題。
