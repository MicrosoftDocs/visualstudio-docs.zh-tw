---
title: 安裝 Visual Studio SDK |Microsoft Docs
description: 瞭解安裝 Visual Studio 軟體發展工具組的選項，包括 Visual Studio 安裝期間。
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5b0d239c2280362b45c085448437b15bd8ddfe8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869527"
---
# <a name="install-the-visual-studio-sdk"></a>安裝 Visual Studio IDE

Visual Studio SDK (軟體發展工具組) 是 Visual Studio 安裝程式中的選擇性功能。 您也可以稍後再安裝 VS SDK。

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>在 Visual Studio 安裝過程中安裝 Visual Studio SDK

若要在 Visual Studio 安裝中包含 VS SDK，請在 **其他工具** 組下安裝 **Visual Studio 延伸模組開發** 工作負載。 此工作負載會安裝 Visual Studio SDK 和必要必要條件。 您可以選取或取消選取 **摘要** 視圖中的元件，以進一步調整安裝。

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>在安裝 Visual Studio 之後安裝 Visual Studio SDK

若要在完成 Visual Studio 安裝之後安裝 Visual Studio SDK，請重新執行 Visual Studio 安裝程式，然後選取 **Visual Studio 延伸模組開發** 工作負載。

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>從解決方案安裝 Visual Studio SDK

如果您在沒有先安裝 VS SDK 的情況下開啟具有擴充性專案的方案，則會出現 [ **安裝遺失功能** ] 對話方塊提示您安裝 **Visual Studio 延伸模組開發** 工作負載：

![安裝延伸模組開發](../extensibility/media/install-extension-development.png "安裝延伸模組開發")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>從命令列安裝 Visual Studio SDK

如同任何 Visual Studio 工作負載或元件，您也可以從命令列安裝 **Visual Studio 延伸模組開發** 工作負載 (識別碼： VisualStudioExtension) 。 如需有關適當命令列參數的詳細資訊，請參閱 [使用命令列參數安裝 Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) ，以及判斷工作負載或元件識別碼的一般指示。

請注意，您必須使用符合已安裝之 Visual Studio 版本的 Visual Studio 安裝程式。 例如，如果您的電腦上已安裝 Visual Studio Enterprise，則必須執行 Visual Studio Enterprise 安裝程式 (*vs_enterprise.exe*) 。
