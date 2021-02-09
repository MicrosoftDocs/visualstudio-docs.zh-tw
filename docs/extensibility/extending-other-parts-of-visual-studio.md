---
title: 擴充 Visual Studio 的其他部分 |Microsoft Docs
description: 瞭解您可以擴充的 Visual Studio UI 部分。 您可以建立 VSPackage、寫入活動記錄檔，以及擴充 [工具箱] 和 [狀態列]。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces
ms.assetid: 27d2f1e1-2503-4aca-9cfc-707abd07ccf0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e21c5b8a3570b4da0cb0286d3c0d6d7c84c2f704
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895839"
---
# <a name="extend-other-parts-of-visual-studio"></a>延伸 Visual Studio 的其他部分

您可以擴充的 Visual Studio UI 有許多部分。 在這裡我們只示範幾個。

## <a name="create-a-vspackage"></a>建立 VSPackage

Visual Studio 擴充性的基本構成要素 Vspackage。  瞭解如何新增 VSPackage：[使用 VSPackage 建立延伸](../extensibility/creating-an-extension-with-a-vspackage.md)模組

## <a name="extend-the-toolbox"></a>擴充工具箱

瞭解如何將新的控制項和其他專案新增至 [工具箱]，以及如何使用 [工具箱] 功能：

- [建立 WPF 工具箱控制項](../extensibility/creating-a-wpf-toolbox-control.md)

- [建立 Windows Forms 工具箱控制項](../extensibility/creating-a-windows-forms-toolbox-control.md)

## <a name="extend-the-status-bar"></a>擴充狀態列

瞭解如何讀取和寫入狀態列和進度列，以及如何提供動畫和其他 UI： [擴充狀態列](../extensibility/extending-the-status-bar.md)。

::: moniker range="vs-2017"

## <a name="create-custom-start-pages"></a>建立自訂起始頁

瞭解如何從頭開始，或從可下載的起始頁範例建立您自己的起始頁： [建立自訂起始頁](../extensibility/creating-a-custom-start-page.md)。

::: moniker-end

## <a name="write-to-the-activity-log"></a>寫入活動記錄

瞭解如何寫入活動記錄： [如何：使用活動記錄](../extensibility/how-to-use-the-activity-log.md)。
