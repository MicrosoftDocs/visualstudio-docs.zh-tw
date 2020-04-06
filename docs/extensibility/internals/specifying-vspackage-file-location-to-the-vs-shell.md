---
title: 將 VS 套件檔案位置指定給 VS 外殼 |微軟文件
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
ms.openlocfilehash: f112da4e79bff06d12472f0af7a3fe47b2f25da4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704983"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>為 VS Shell 指定 VSPackage 檔案位置
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必須能夠定位程式集 DLL 以載入 VS 套件。 您可以以各種方式找到它,如下表所述。

| 方法 | 描述 |
| - | - |
| 使用 CodeBase 註冊表項。 | CodeBase 金鑰可用於從任何完全[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]限定 的檔路徑直接載入 VSPackage 程式集。 鍵的值應該是 DLL 的檔路徑。 這是載入[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]包程式集的最佳方式。 此技術有時稱為"CodeBase/私有安裝目錄技術」。 在註冊期間,代碼庫的值通過<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext>類型的實例傳遞給註冊屬性類。 |
| 將 DLL 放入**私有程式集**目錄中。 | 將程式集放在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]目錄的**私有程式集**子目錄中。 將自動檢測到**位於私有程式集中的程式集**,但在 **「添加引用**」對話框中不可見。 **私有程式集**與**公共程式集**之間的區別是,在 **'新增引用'** 對話框中列舉**公共程式集中的程式集**。 如果您選擇不使用"CodeBase/私有安裝目錄"技術,則應安裝到**PrivateAssemblies**目錄中。 |
| 使用強命名的程式集和程式集註冊表項。 | 程式集鍵可用於顯式定向[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]載入強命名的 VSPackage 程式集。 鍵的值應為程式集的強名稱。 |
| 將 DLL 放入**公共程式集**目錄中。 | 最後,程式集也可以放置在**公共程式集**子目錄中。 自動偵測在**公共程式集中的程式集**,並且也會顯示在中的 **「新增參考」** 對話框中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。<br /><br /> 僅當 VSPackage 程式集包含旨在供其他 VSPackage 開發人員重用的託管元件時,才應將其放在**PublicAssemblies**目錄中。 大多數程式集不符合此條件。 |

> [!NOTE]
> 對所有從屬程式集使用強命名、簽名程式集。 這些程式集也應安裝在您自己的目錄或全域程式集緩存 (GAC) 中。 這樣可以防止與具有相同基本檔名(稱為弱名綁定)的程式集發生衝突。
