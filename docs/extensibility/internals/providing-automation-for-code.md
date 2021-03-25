---
title: 為程式碼提供自動化 |Microsoft Docs
description: 瞭解如何執行程式碼模型，它需要執行由內部資料結構所決定的介面。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 57d5337ae088560bb94a6af39902e90b6af02686
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060961"
---
# <a name="providing-automation-for-code"></a>為程式碼提供自動化
不需要為您的程式碼建立 automation 模型。 環境 SDK 不提供執行此動作的範例。 若要深入瞭解程式碼模型，請參閱 <xref:EnvDTE.CodeModel> 物件。

 若要執行程式碼模型，您必須執行內部資料結構所決定的任何介面。 物件必須衍生自 `IDispatch` 類別。

 您可以從物件取得您延伸的物件， <xref:EnvDTE.CodeModel> 以及 <xref:EnvDTE.FileCodeModel> 可從物件取得的物件，如下 <xref:EnvDTE.Project> 所示：

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 您可以選擇只在 `CodeModel` `FileCodeModel` 您從和物件傳回的物件中，執行或介面 `Project` <xref:EnvDTE.ProjectItem> 。 提供此介面適用于您專案系統的任何功能。

 如果您想要新增標準和介面中無法使用的功能，例如方法或屬性， `CodeModel` `FileCodeModel` 請建立繼承自標準的介面。 請務必將它記錄在您的專案系統中，讓終端使用者知道要尋找它。 您會傳回標準介面，但使用者可以呼叫方法， `QueryInterface` 或將它轉換為您的介面（如果已知存在的話）。

## <a name="see-also"></a>另請參閱
- [自動化模型概觀](../../extensibility/internals/automation-model-overview.md)
