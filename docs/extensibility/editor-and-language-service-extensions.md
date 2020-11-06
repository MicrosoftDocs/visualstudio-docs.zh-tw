---
title: 編輯器和語言服務延伸模組 |Microsoft Docs
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
ms.openlocfilehash: 78d85cd3651f8769104a61586bea1468e1c21cd2
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414070"
---
# <a name="editor-and-language-service-extensions"></a>編輯器和語言服務延伸模組
您可以擴充 Visual Studio 程式碼編輯器的大部分功能。 編輯器是以 Windows Presentation Foundation (WPF) 為基礎，而且是以 managed 程式碼撰寫。 雖然此設計與舊版 Visual Studio 的設計不同，但它會提供大部分相同的功能。 若要擴充編輯器，請使用 Managed Extensibility Framework (MEF) 。

 Visual Studio SDK 提供稱為 *填充* 碼的介面卡，以支援針對較早版本所撰寫的 vspackage。 儘管如此，如果您有現有的 VSPackage，我們建議您將其更新為新的技術，以取得更佳的效能和可靠性。

## <a name="related-topics"></a>相關主題

|Title|描述|
|-----------|-----------------|
|[使用編輯器專案範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)|使用編輯器專案範本的簡介。|
|[擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)|檔的連結，這些檔會介紹核心編輯器的設計和功能，並示範如何擴充。|
|[編輯器中的舊版介面](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)|說明如何從現有程式碼存取核心編輯器的檔連結。|
|[建立自訂編輯器和設計工具](../extensibility/creating-custom-editors-and-designers.md)|說明如何建立自訂編輯器的檔連結。|
|[舊版語言服務擴充性](../extensibility/internals/legacy-language-service-extensibility.md)|說明如何將程式設計語言整合至 Visual Studio 的檔連結。|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|介紹 (MEF) 的 Managed Extensibility Framework。|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|介紹 WPF) 的 Windows Presentation Foundation (。|