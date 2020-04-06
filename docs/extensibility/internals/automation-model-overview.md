---
title: 自動化模型概述 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710013"
---
# <a name="automation-model-overview"></a>自動化模型概述
自動化模型由一組物件組成,您可以編寫 Visual Studio 外接程式或擴展。 外接程式是一個可以操作 Visual Studio 環境並自動執行常見任務的應用程式。 Visual Studio 延伸可以建立自訂 Visual Studio 元件或添加到標準元件(如文字編輯器)的功能。

## <a name="objects-in-the-automation-model"></a>自動化模型中的物件
 自動化模型由控制公共環境主要方面的相關對象組組成。 下圖顯示了組成自動化模型的大量 Visual Studio 物件。

 ![視覺化工作室自動化物件圖](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudio自動化物件圖表")

 有關詳細資訊,請參閱[擴展可視化工作室環境](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)。

 環境為不同的功能區域提供了一個模型。 例如,在代碼中可以找到各種元素的代碼模型。 有各種文件元素的文檔模型。 一個領域,即項目區域,對 VSPackage 提供者特別感興趣。 您可能希望新的項目類型以與自動化模型相同的方式[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]對自動化[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]模型 做出貢獻。 該過程在[提供 VSPackages 的自動化](../../extensibility/internals/providing-automation-for-vspackages.md)中進行了概述。

 可以考慮延伸環境自動化模型的位置:

- 隨附此逐步解說的專案

- Document

- 程式碼

- 組建

有關自動化的詳細資訊,請參閱[可視化工作室的自動化和可擴充性](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015)。 本文檔及其提供的連結可説明您做出有關如何為 VSPackage 提供自動化的決策。

## <a name="see-also"></a>另請參閱
- [如何:建立外接程式](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
