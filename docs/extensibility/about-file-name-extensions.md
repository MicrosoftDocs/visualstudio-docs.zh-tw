---
title: 關於檔案名副檔名 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03e07ec233ef975441a1f10507f0db872051558f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740354"
---
# <a name="about-file-name-extensions"></a>關於檔案名副檔名
註冊 VSPackage 的檔副檔名時,將其[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]與的版本 相關聯。 若電腦上安裝了多個版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

 VS包的檔副檔名在**HKEY_CLASSES_ROOT**鍵下註冊,預設值指向關聯的程式設計標識符 (ProgID)。

 下面的範例顯示 *.vcproj*檔副檔名的註冊資訊:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 與 關聯[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的檔案必須具有版本化的 ProgID,`VisualStudio.vcproj.8.0`如 。 版本化 ProgID 允許產品並行安裝,以維護產品版本之間的檔擴展關聯。 特定於版本的 ProgID 還允許您使用標準的無字(如開啟、編輯等),而無需擔心覆蓋或被其他應用程式[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]或版本覆蓋 。

 在某些情況下,不應更改與文件擴展名關聯的 ProgID。 例如 *,.htm*檔副檔名(progid = htmlfile)的 ProgID 在作業系統中的多個位置進行硬編碼,並且與 *.htm*和 *.html*檔關聯廣為人知和使用。

## <a name="see-also"></a>另請參閱
- [註冊並行部署的檔案名副檔名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [為檔案名副檔名指定檔案處理程式](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
