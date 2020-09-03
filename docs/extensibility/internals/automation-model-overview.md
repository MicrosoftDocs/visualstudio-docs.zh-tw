---
title: Automation 模型總覽 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b940677c370106ebdcc63c7984d553003251e8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710013"
---
# <a name="automation-model-overview"></a>Automation 模型總覽
Automation 模型包含一組物件，可讓您撰寫 Visual Studio 的增益集或延伸模組。 增益集是一種應用程式，可操作 Visual Studio 環境並將一般工作自動化。 Visual Studio 擴充功能可以建立自訂 Visual Studio 元件，或新增至標準元件的功能，例如文字編輯器。

## <a name="objects-in-the-automation-model"></a>Automation 模型中的物件
 Automation 模型包含可控制常見環境之主要 facet 的相關物件群組。 下圖顯示組成 automation 模型的一組廣泛 Visual Studio 物件。

 ![Visual Studio automation 物件圖](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 如需詳細資訊，請參閱 [擴充 Visual Studio 環境](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)。

 環境會針對不同的功能區域提供模型。 比方說，您可能會在程式碼中找到各種專案的程式碼模型。 有各種檔元素的檔模型。 VSPackage 提供者特別感興趣的一個區域（專案區域）。 您可能會想要讓新的專案類型能夠以 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 和參與 automation 模型的相同方式，來參與 automation 模型 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 。 此程式會在 [提供自動化的 vspackage](../../extensibility/internals/providing-automation-for-vspackages.md)中概述。

 您可以考慮延伸環境自動化模型的位置：

- 專案

- Document

- 程式碼

- Build

如需自動化的詳細資訊，請參閱 [Visual Studio 的自動化和](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015)擴充性。 這份檔及其提供的連結，可協助您做出有關如何為 VSPackage 提供自動化的決策。

## <a name="see-also"></a>另請參閱
- [如何：建立增益集](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
