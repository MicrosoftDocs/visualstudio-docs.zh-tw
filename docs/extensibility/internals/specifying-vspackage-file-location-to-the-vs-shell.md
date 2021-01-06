---
title: 對 VS Shell 指定 VSPackage 檔案位置 |Microsoft Docs
description: 瞭解如何讓 Visual Studio 找出元件 DLL 以載入 VSPackage。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e59bea4894d6b0014542ea2a32bf6c73bc8d797c
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877854"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>為 VS Shell 指定 VSPackage 檔案位置
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 必須能夠找出元件 DLL 以載入 VSPackage。 您可以用各種方式找出它，如下表所述。

| 方法 | 描述 |
| - | - |
| 使用程式碼基底登錄機碼。 | 您可以使用程式碼基底索引鍵， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 從任何完整的檔案路徑載入 VSPackage 元件。 機碼的值應該是 DLL 的檔案路徑。 這是 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 載入封裝元件的最佳方式。 這項技術有時也稱為「程式碼基底/私用安裝目錄技術」。 在註冊期間，程式碼基底的值會透過型別的實例傳遞給註冊屬性類別 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> 。 |
| 將 DLL 放在 **PrivateAssemblies** 目錄中。 | 將元件放在目錄的 **PrivateAssemblies** 子目錄中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 系統會自動偵測位於 **PrivateAssemblies** 中的元件，但是不會顯示在 [ **加入參考** ] 對話方塊中。 **PrivateAssemblies** 和 **PublicAssemblies** 之間的差異在於， **PublicAssemblies** 中的元件是在 [**加入參考**] 對話方塊中列舉。 如果您選擇不使用「程式碼基底/私用安裝目錄」技術，則應該將安裝到 **PrivateAssemblies** 目錄中。 |
| 使用強式名稱的元件和元件登錄機碼。 | 元件索引鍵可用來明確地指示 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 載入強式名稱的 VSPackage 元件。 索引鍵的值應該是元件的強式名稱。 |
| 將 DLL 放在 **PublicAssemblies** 目錄中。 | 最後，元件也可以放在 **PublicAssemblies** 子目錄中。 系統會自動偵測位於 **PublicAssemblies** 中的元件，而且也會出現在的 [ **加入參考** ] 對話方塊中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。<br /><br /> 如果 VSPackage 元件包含要供其他 VSPackage 開發人員重複使用的 managed 元件，則應該只放置在 **PublicAssemblies** 目錄中。 大部分的元件不符合此準則。 |

> [!NOTE]
> 針對所有相依元件使用強式名稱的已簽署元件。 這些元件也應該安裝在您自己的目錄或全域組件快取 (GAC) 中。 這可防止與具有相同基底檔案名的元件發生衝突，也就是所謂的弱式名稱系結。
