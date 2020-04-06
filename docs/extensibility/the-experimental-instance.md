---
title: 實驗實例 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e2284767a0aa6be58c0f7e38c912783728914cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699032"
---
# <a name="the-experimental-instance"></a>實驗執行個體
為了保護您的 Visual Studio 開發環境免受可能更改它的未經測試的應用程式的影響,VSSDK 提供了一個實驗空間,可用於實驗。 像往常一樣使用 Visual Studio 來開發新應用程式,但使用此實驗實例運行它們。

 每個具有 VSIX 套件的應用程式都會在除錯模式下啟動 Visual Studio 實驗實例。

 如果要在特定解決方案之外啟動 Visual Studio 的實驗實例,在命令視窗中執行以下命令:

 "*\<視覺工作室安裝路徑>*[公共7_IDE_devenv.exe] /RootSuffix Exp

> [!NOTE]
> 實驗實例寫入`<version number>Exp``<version number>Exp_Config`和節點下的註冊表。 例如,Visual Studio 2015 實驗註冊表區域是
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` 和 `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 我們建議您在開發擴展時在實驗實例中運行擴展。 部署擴展時,它將在開發實例中運行。 有關註冊應用程式的詳細資訊,請參閱[註冊 VS 包](../extensibility/internals/registering-vspackages.md)。
