---
title: 安裝 Visual Studio SDK |Microsoft Docs
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 664ecb57a326938345c2c313228c813293230b7e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711744"
---
# <a name="install-the-visual-studio-sdk"></a>安裝 Visual Studio IDE

Visual Studio SDK （軟體開發套件） 是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio 安裝過程中安裝 Visual Studio SDK

若要併入您的 Visual Studio 安裝中的 VS SDK，請安裝**Visual Studio 延伸模組開發**下的工作負載**其他工具組**。 此工作負載會安裝 Visual Studio SDK 及所需的必要條件。 您可以進一步微調安裝選取或取消選取的元件**摘要**檢視。

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>安裝 Visual Studio 之後安裝 Visual Studio SDK

若要安裝 Visual Studio SDK，完成您的 Visual Studio 安裝之後，重新執行 Visual Studio 安裝程式，然後選取**Visual Studio 延伸模組開發**工作負載。

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>從方案安裝 Visual Studio SDK

如果您使用的擴充性專案中開啟的方案，但是未先安裝 VS SDK，您將會提示所**安裝遺漏的功能**對話方塊，即可安裝**Visual Studio 延伸模組開發**工作負載：

![安裝延伸模組開發](../extensibility/media/install-extension-development.png "安裝延伸模組開發")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>從命令列安裝 Visual Studio SDK

如有任何 Visual Studio 工作負載或元件，您也可以安裝**Visual Studio 延伸模組開發**工作負載 (識別碼：Microsoft.VisualStudio.Workload.VisualStudioExtension) 從命令列。 請參閱[使用命令列參數安裝 Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)如需有關適當的命令列參數和判斷工作負載或元件識別碼的一般指示。

請注意，您必須使用符合您已安裝 Visual Studio 版本的 Visual Studio 安裝程式。 例如，如果您有在電腦上安裝的 Visual Studio Enterprise，您必須執行 Visual Studio Enterprise 安裝程式 (*vs_enterprise.exe*)。