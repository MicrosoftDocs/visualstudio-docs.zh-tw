---
title: 實驗執行個體 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c4aa7e8e74ccb8f31dc2320192cf088b5391678
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685114"
---
# <a name="the-experimental-instance"></a>實驗執行個體
為了確保您的 Visual Studio 開發環境，從未經測試的應用程式可能會變更，請 VSSDK 提供實驗性的空間，可供您實驗。 像往常一樣，使用 Visual Studio 開發新的應用程式，但您使用此實驗的執行個體執行。

 VSIX 封裝每個應用程式會啟動偵錯模式中的 Visual Studio 實驗執行個體。

 如果您想要開始在特定的方案之外的 Visual Studio 實驗執行個體，請在命令視窗執行下列命令：

 "*\<Visual studio installation path>* \Common7\IDE\devenv.exe" /RootSuffix Exp

> [!NOTE]
>  實驗性的執行個體底下的登錄寫入`<version number>Exp`和`<version number>Exp_Config`節點。 例如 Visual Studio 2015 實驗登錄區是
>
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` 和 `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 我們建議您在實驗執行個體中執行您的延伸模組，在開發過程。 當您部署延伸模組時，它會在開發執行個體中執行。 如需有關如何註冊應用程式的詳細資訊，請參閱 <<c0> [ 註冊 Vspackage](../extensibility/internals/registering-vspackages.md)。