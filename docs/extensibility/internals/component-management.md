---
title: 元件管理 |Microsoft Docs
description: 瞭解如何在 Visual Studio 中建立 VSPackage 安裝程式時，管理 Windows Installer 元件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9767af4c30957111526303600f9e8eda815b42f0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057087"
---
# <a name="component-management"></a>元件管理
Windows Installer 中的工作單位稱為 Windows Installer 元件 (有時候稱為 WICs 或只是) 的元件。 GUID 會識別每個 WIC，也就是使用 Windows Installer 的安裝程式和參考計數的基本單位。

 雖然您可以使用數個產品來建立 VSPackage 安裝程式，但這項討論會假設使用 Windows Installer (*.msi*) 檔。 當您建立安裝程式時，必須正確地管理檔案部署，以便正確的參考計數會在任何時間發生。 因此，不同版本的產品在安裝和卸載案例中不會干擾或互相中斷。

 在 Windows Installer 中，參考計數會發生在元件層級。 您必須仔細地將資源（檔案、登錄專案等等）組織成元件。 還有其他層級的組織（例如模組、功能和產品）可在不同的案例中有所説明。 如需詳細資訊，請參閱 [Windows Installer 基本概念](../../extensibility/internals/windows-installer-basics.md)。

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>針對並存安裝撰寫安裝程式的指導方針

- 將在版本之間共用的檔案和登錄機碼，寫入自己的元件。

     這麼做可讓您輕鬆地在下一版中使用。 例如，在全域註冊的類型程式庫、副檔名、在 **HKEY_CLASSES_ROOT** 中註冊的其他專案等等。

- 將共用元件群組至不同的合併模組。

     這項策略可協助您正確地撰寫，以供並存安裝繼續進行。

- 使用相同的 Windows Installer 元件在各版本之間，安裝共用檔案和登錄機碼。

     如果您使用不同的元件，則會在其中一個已建立版本的 VSPackage 卸載，但仍安裝另一個 VSPackage 時，卸載檔案和登錄專案。

- 請勿混用相同元件中的版本設定和共用專案。

     這麼做可讓您無法將共用專案安裝到全域位置，並將版本設定的專案安裝到隔離的位置。

- 沒有指向已建立版本之檔案的共用登錄機碼。

     如果您這麼做，則在安裝另一個已建立版本的 VSPackage 時，將會覆寫共用金鑰。 移除第二個版本之後，索引鍵指向的檔案就會消失。

## <a name="see-also"></a>另請參閱
- [在共用和建立版本的 Vspackage 之間進行選擇](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [VSPackage 安裝案例](../../extensibility/internals/vspackage-setup-scenarios.md)
