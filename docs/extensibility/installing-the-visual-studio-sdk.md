---
title: 安裝 Visual Studio SDK |Microsoft Docs
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31df92b011336320d759461ed16ce2a3c8f61017
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905540"
---
# <a name="install-the-visual-studio-sdk"></a>安裝 Visual Studio IDE

Visual Studio SDK （軟體發展工具組）是 Visual Studio 安裝程式中的選用功能。 您稍後也可以安裝 VS SDK。

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>安裝 Visual Studio SDK 作為 Visual Studio 安裝的一部分

若要在您的 Visual Studio 安裝中包含 VS SDK，請在**其他工具**組下安裝**Visual Studio 延伸模組開發**工作負載。 此工作負載會安裝 Visual Studio SDK 和必要的必要條件。 您可以從 [**摘要**] 視圖中選取或取消選取 [元件]，以進一步調整安裝。

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>安裝之後，請安裝 Visual Studio SDK Visual Studio

若要在完成您的 Visual Studio 安裝之後安裝 Visual Studio SDK，請重新執行 Visual Studio 安裝程式，然後選取 [ **Visual Studio 延伸模組開發**] 工作負載。

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>從解決方案安裝 Visual Studio SDK

如果您在未先安裝 VS SDK 的情況下，使用擴充性專案開啟方案，系統會提示您安裝 [**缺少功能**] 對話方塊，以安裝**Visual Studio 延伸模組開發**工作負載：

![安裝延伸模組開發](../extensibility/media/install-extension-development.png "安裝延伸模組開發")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>從命令列安裝 Visual Studio SDK

如同任何 Visual Studio 工作負載或元件，您也可以從命令列安裝**Visual Studio 延伸模組開發**工作負載（識別碼： VisualStudio）。 如需適當命令列參數的詳細資訊，以及決定工作負載或元件識別碼的一般指示，請參閱[使用命令列參數來安裝 Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) 。

請注意，您必須使用符合已安裝之 Visual Studio 版本的 Visual Studio 安裝程式。 例如，如果您已在電腦上安裝 Visual Studio Enterprise，則必須執行 Visual Studio Enterprise 安裝程式（*vs_enterprise.exe*）。
