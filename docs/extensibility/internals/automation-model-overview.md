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
ms.openlocfilehash: 83df8926be9cd7217c514a2ed3f242bf8e121913
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584564"
---
# <a name="automation-model-overview"></a>Automation 模型總覽
Automation 模型包含一組物件，可讓您撰寫 Visual Studio 的增益集或延伸模組。 增益集是一種應用程式，可操作 Visual Studio 環境並將一般工作自動化。 Visual Studio 擴充功能可以建立自訂 Visual Studio 元件，或新增至標準元件的功能，例如文字編輯器。

## <a name="objects-in-the-automation-model"></a>Automation 模型中的物件
 Automation 模型包含可控制常見環境之主要 facet 的相關物件群組。 下圖顯示組成 automation 模型的一組廣泛 Visual Studio 物件。

 ![Visual Studio automation 物件圖](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 如需詳細資訊，請參閱 [擴充 Visual Studio 環境](/previous-versions/esk3eey8(v=vs.140))。

 環境會針對不同的功能區域提供模型。 比方說，您可能會在程式碼中找到各種專案的程式碼模型。 有各種檔元素的檔模型。 VSPackage 提供者特別感興趣的一個區域（專案區域）。 您可能會想要讓新的專案類型能夠以 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 和參與 automation 模型的相同方式，來參與 automation 模型 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 。 此程式會在 [提供自動化的 vspackage](../../extensibility/internals/providing-automation-for-vspackages.md)中概述。

 您可以考慮延伸環境自動化模型的位置：

- Project

- 文件

- 程式碼

- 組建

如需自動化的詳細資訊，請參閱 [Visual Studio 的自動化和](../../vs-2015/extensibility/extensibility-in-visual-studio.md?view=vs-2015&preserve-view=true)擴充性。 這份檔及其提供的連結，可協助您做出有關如何為 VSPackage 提供自動化的決策。

## <a name="see-also"></a>另請參閱
- [如何：建立增益集](/previous-versions/80493a3w(v=vs.140))