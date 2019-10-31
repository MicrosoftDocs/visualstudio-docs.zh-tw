---
title: Automation 模型總覽 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ea38dc79bd557f17bbae8276dd112304c9a40fa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186731"
---
# <a name="automation-model-overview"></a>Automation 模型總覽
Automation 模型包含一組物件，您可以用它來撰寫 Visual Studio 增益集或延伸模組。 增益集是一種應用程式，可以操作 Visual Studio 環境，並將一般工作自動化。 Visual Studio 延伸模組可以建立自訂 Visual Studio 元件，或加入標準元件（例如文字編輯器）的功能。

## <a name="objects-in-the-automation-model"></a>Automation 模型中的物件
 Automation 模型包含可控制通用環境之主要 facet 的相關物件群組。 下圖顯示組成 automation 模型的一組廣泛 Visual Studio 物件。

 ![Visual Studio automation 物件圖表](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 如需詳細資訊，請參閱[擴充 Visual Studio 環境](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)。

 環境會針對不同的功能區域提供模型。 例如，您可能會在程式碼中找到的各種元素有一個程式碼模型。 有各種檔元素的檔模型。 VSPackage 提供者會特別注意一個區域，即專案區域。 您可能會想要讓新的專案類型參與 automation 模型，其方式與 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 和 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 對自動化模型的貢獻非常類似。 該程式會在為[Vspackage 提供自動化](../../extensibility/internals/providing-automation-for-vspackages.md)中概述。

 您可以考慮擴充環境自動化模型的地方：

- 專案

- 文件

- 程式碼

- 組建

如需自動化的詳細資訊，請參閱[Visual Studio 的自動化和](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015)擴充性。 本檔及其提供連結的檔，可協助您決定如何為 VSPackage 提供自動化。

## <a name="see-also"></a>請參閱
- [如何：建立增益集](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)