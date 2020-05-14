---
title: 編輯器和語言服務擴展 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e37165dc5fe9ac010545304218e807d923b424b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712026"
---
# <a name="editor-and-language-service-extensions"></a>編輯器和語言服務擴充
您可以擴展 Visual Studio 代碼編輯器的大多數功能。 編輯器基於 Windows 示範基礎 (WPF),以託管代碼編寫。 儘管此設計不同於早期版本的 Visual Studio 的設計,但它提供了大多數相同的功能。 要延伸編輯器,請使用託管擴充性框架 (MEF)。

 Visual Studio SDK 提供稱為*hims*的適配器,以支援為早期版本編寫的 VS 包。 但是,如果您有現有的 VSPackage,我們建議您將其更新到新技術,以獲得更好的性能和可靠性。

## <a name="related-topics"></a>相關主題

|Title|描述|
|-----------|-----------------|
|[使用編輯器項目建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)|使用編輯器項範本的簡介。|
|[延伸編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)|指向文檔的連結,這些文檔介紹了核心編輯器的設計和功能,並演示如何擴展它。|
|[編輯器中的舊介面](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)|指向解釋如何從現有代碼訪問核心編輯器的文檔的連結。|
|[建立自訂編輯器和設計器](../extensibility/creating-custom-editors-and-designers.md)|指向解釋如何創建自定義編輯器的文件的連結。|
|[傳統語言服務可擴充性](../extensibility/internals/legacy-language-service-extensibility.md)|指向描述如何將程式設計語言整合到 Visual Studio 的文件的連結。|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|介紹託管擴展性框架 (MEF)。|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|介紹 Windows 演示基礎 (WPF)。|
