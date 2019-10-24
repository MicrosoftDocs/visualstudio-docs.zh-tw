---
title: 為程式碼提供自動化 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 874446aa6bf2e40a120aac49e7d91fd3d861d1d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724967"
---
# <a name="providing-automation-for-code"></a>為程式碼提供自動化
不需要為您的程式碼建立自動化模型。 環境 SDK 不會提供執行此作業的範例。 如需深入瞭解程式碼模型，請參閱 <xref:EnvDTE.CodeModel> 物件。

 若要執行程式碼模型，您必須執行由內部資料結構決定的任何介面。 物件必須衍生自 `IDispatch` 類別。

 您擴充、<xref:EnvDTE.CodeModel> 和 <xref:EnvDTE.FileCodeModel> 的物件可從 <xref:EnvDTE.Project> 物件取得，如下所示：

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 您可以選擇只在從 `Project` 和 <xref:EnvDTE.ProjectItem> 物件傳回的物件中，執行 `CodeModel` 或 `FileCodeModel` 介面。 從這個介面提供適用于您專案系統的任何功能。

 如果您想要新增標準 `CodeModel` 無法使用的功能（例如方法或屬性），並 `FileCodeModel` 介面，請建立繼承自標準的自訂介面。 請務必將它記錄到您的專案系統，讓終端使用者知道要尋找它。 您會傳回標準介面，但使用者可以呼叫 `QueryInterface` 方法，或將它轉換成您的介面（如果已知存在的話）。

## <a name="see-also"></a>請參閱
- [Automation 模型概觀](../../extensibility/internals/automation-model-overview.md)