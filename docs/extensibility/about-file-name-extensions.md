---
title: 關於副檔名 |Microsoft Docs
description: 瞭解如何為 Vspackage 註冊副檔名，並將其與特定版本的 Visual Studio 建立關聯。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3f938eb31c06e1e88af21b058b4475bc192d49c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874400"
---
# <a name="about-file-name-extensions"></a>關於副檔名
當您註冊 VSPackage 的副檔名時，會將它與的版本建立關聯 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 如果電腦上安裝了一個以上的版本，這就很重要 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

 Vspackage 的副檔名是在 **HKEY_CLASSES_ROOT** 機碼下註冊，其預設值會指向 (ProgID) 的相關聯程式設計識別碼。

 下列範例顯示 *vcproj* 副檔名的註冊資訊：

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 與相關聯的檔案 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 必須具有已建立版本的 ProgID，例如 `VisualStudio.vcproj.8.0` 。 已建立版本的 ProgID 允許產品的並存安裝，以維護產品版本之間的副檔名關聯。 版本特定的 ProgID 也可讓您使用標準動詞，例如開啟、編輯等，而不需要考慮其他應用程式或版本的覆寫或覆寫 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

 在某些情況下，與副檔名相關聯的 ProgID 不應變更。 例如， *.htm* 副檔名 (progid = htmlfile) 的 progid 會以作業系統中的數個位置進行硬式編碼，並且可與 *.htm* 和 *.html* 檔案相關聯。

## <a name="see-also"></a>另請參閱
- [註冊並存部署的副檔名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [指定副檔名的檔案處理常式](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
