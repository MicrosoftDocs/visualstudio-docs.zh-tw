---
title: 提供代碼自動化 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd13b7db2065069ff1540dbfc921570c2b230b8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705985"
---
# <a name="providing-automation-for-code"></a>為程式碼提供自動化
不需要為代碼創建自動化模型。 環境 SDK 不提供執行此操作的範例。 有關程式碼模型的見解,請參閱<xref:EnvDTE.CodeModel>物件 。

 要實現代碼模型,必須實現由內部數據結構確定的任何介面。 物件必須派生自類`IDispatch`。

 擴<xref:EnvDTE.CodeModel>充 的<xref:EnvDTE.FileCodeModel>物件 和<xref:EnvDTE.Project>可從 物件 獲得,如下所示:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 `CodeModel`您可以選擇僅實現從`FileCodeModel``Project`<xref:EnvDTE.ProjectItem>和物件傳回的物件中的 或介面。 提供適合項目系統的任何介面功能。

 如果要添加標準和`CodeModel``FileCodeModel`介面中不可用的功能(如方法或屬性),請創建從標準繼承自己的介面。 請務必使用專案系統進行文檔記錄,以便最終使用者知道查找它。 返回標準介面,但用戶可以調用`QueryInterface`方法或強制轉換到您的介面(如果已知存在)。

## <a name="see-also"></a>另請參閱
- [自動化模型概觀](../../extensibility/internals/automation-model-overview.md)
