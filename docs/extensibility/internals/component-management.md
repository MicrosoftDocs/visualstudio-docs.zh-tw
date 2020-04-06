---
title: 元件管理 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5dcac9fb14a83021b852be2c52436fcdca84bf5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709329"
---
# <a name="component-management"></a>元件管理
Windows 安裝程式中的任務單元稱為 Windows 安裝程式元件(有時稱為 WIC 或只是元件)。 GUID 識別每個 WIC,這是使用 Windows 安裝程式的安裝和引用計數的基本單元。

 儘管可以使用多個產品創建 VSPackage 安裝程式,但此討論假定使用 Windows 安裝程式 *(.msi*) 檔。 創建安裝程式時,必須正確管理檔部署,以便隨時進行正確的引用計數。 因此,在安裝和卸載混合方案中,產品的不同版本不會相互干擾或破裂。

 在 Windows 安裝程式中,引用計數發生在元件級別。 您必須仔細將資源(文件、註冊表項等)組織到元件中。 還有其他級別的組織(如模組、功能和產品)可以在不同方案中提供説明。 有關詳細資訊,請參閱[Windows 安裝程式基礎知識](../../extensibility/internals/windows-installer-basics.md)。

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>並行安裝的創作設定指南

- 創作在版本之間共用的檔和註冊表項到其自己的元件中。

     這樣做允許您在下一版本中輕鬆使用它們。 例如,鍵入全域註冊的庫、檔副檔名、**在HKEY_CLASSES_ROOT**中註冊的其他專案等。

- 將共享元件分組到單獨的合併模組中。

     此策略可説明您正確創作並行安裝。

- 跨版本使用相同的 Windows 安裝程式元件安裝共用檔和註冊表項。

     如果使用其他元件,則在卸載一個版本化的 VSPackage 但仍安裝另一個 VSPackage 時,將卸載檔和註冊表項。

- 不要在同一元件中混合版本控制專案和共用專案。

     這樣,就無法將共用專案安裝到全域位置,並將專案版本控制到隔離位置。

- 沒有指向版本化檔的共享註冊表項。

     如果這樣做,則在安裝另一個版本化的 VSPackage 時,共用密鑰將被覆蓋。 刪除第二個版本後,鍵指向的檔將消失。

## <a name="see-also"></a>另請參閱
- [在分享與版本化 VS 套件之間進行選擇](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [VS 套件設定機制](../../extensibility/internals/vspackage-setup-scenarios.md)
