---
title: 安裝視覺化工作室 SDK |微軟文件
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f391708abbd8a9b66f2dfd5aaa6559cb075910d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710351"
---
# <a name="install-the-visual-studio-sdk"></a>安裝 Visual Studio IDE

可視化工作室 SDK(軟體開發工具組)是可視化工作室設置中的可選功能。 以後還可以安裝 VS SDK。

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>安裝視覺化工作室 SDK 作為視覺化工作室安裝的一部分

要將 VS SDK 包含在可視化工作室安裝中,請在 **「其他工具集**」下安裝**Visual Studio 擴展開發**工作負載。 此工作負載將安裝可視化工作室 SDK 和必要的先決條件。 您可以通過從 **「摘要」** 檢視中選擇或取消選擇元件來進一步調整安裝。

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>安裝視覺工作室後安裝可視化工作室 SDK

要在完成 Visual Studio 安裝後安裝 Visual Studio SDK,請重新運行 Visual Studio 安裝程式並選擇**Visual Studio 擴展開發**工作負載。

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>從解決方案安裝視覺化工作室 SDK

如果在未首先安裝 VS SDK 的情況下開啟具有擴充性項目的解決方案,系統將提示**安裝缺少功能對話框**以安裝 Visual Studio**擴充開發**工作負荷:

![安裝延伸開發](../extensibility/media/install-extension-development.png "安裝延伸開發")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>從命令列安裝視覺化工作室 SDK

與任何 Visual Studio 工作負載或元件一樣,您還可以從命令行安裝**Visual Studio 擴展開發**工作負載(ID:Microsoft.VisualStudio.工作負荷.VisualStudio 擴展)。 有關適當的命令列交換機的詳細資訊以及有關確定工作負載或元件標識符的一般說明,請參閱[使用命令列參數安裝 Visual Studio。](../install/use-command-line-parameters-to-install-visual-studio.md)

請注意,您必須使用與已安裝版本的 Visual Studio 相匹配的可視化工作室安裝程式。 例如,如果電腦上安裝了 Visual Studio 企業版,則必須運行可視化工作室企業安裝程式 *(vs_enterprise.exe*)。
