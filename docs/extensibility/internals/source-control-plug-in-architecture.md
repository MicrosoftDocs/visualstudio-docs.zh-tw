---
title: 源代碼管理外掛程式架構 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f549ad2c4ee456860a08fbf20ccda813934a8582
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705101"
---
# <a name="source-control-plug-in-architecture"></a>原始檔控制外掛程式架構
您可以透過實作及附加原始程式碼管理[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]外掛程式, 向整合式開發環境 (IDE) 添加原始程式碼管理支援。 IDE 通過定義良好的原始程式碼管理外掛程式 API 連接到原始碼管理外掛程式。 IDE 透過提供由工具列和功能表命令組成的使用者介面(UI) 來公開原始程式碼管理系統的版本控制功能。 原始程式碼管理外掛程式實現原始程式碼管理功能。

## <a name="source-control-plug-in-resources"></a>原始程式碼管理外掛程式資源
 原始程式碼管理外掛程式提供資源來幫助創建版本控制應用程式並將其[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]連接到 IDE。 原始碼管理外掛程式包含必須由原始碼管理外掛程式的 API 規範,以便它可以整合到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 中 。 它還包含一個代碼示例(用C++編寫),該示例實現了骨架原始程式碼管理外掛程式,演示了符合原始程式碼管理外掛程式API的基本功能的實現。

 原始程式碼管理外掛程式 API 規範允許您使用您選擇的任何原始碼管理系統,如果您建立原始碼管理 DLL 與根據原始碼管理外掛程式 API 實現所需的函數集。

## <a name="components"></a>元件
 關係圖中的原始碼管理配配器包是IDE的元件,該元件將使用者對原始程式碼管理操作的請求轉換為原始程式碼管理外掛程式支援的函數調用。 要做到這一點,IDE 和原始程式碼管理外掛程式必須有一個有效的對話方塊,在IDE和外掛程式之間來回傳遞資訊。 要進行此對話框,它們都必須講同一種語言。 本文件中概述的原始程式碼管理外掛程式 API 是此交換的常見詞彙表。

 ![源碼控制結構圖](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch")顯示 VS 與原始碼管理外掛程式之間互動的架構結構圖

 如體系結構圖所示,在關係圖[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中標記為 VS shell 的 shell 承載使用者的工作項目和相關元件(如編輯器和解決方案資源管理器)。 原始程式碼管理介面管理介面管理外掛程式之間的互動。 原始程式碼管理配接器套件提供其自己的原始程式碼管理 UI。 它是使用者交互以啟動和定義原始程式碼管理操作範圍的頂級 UI。

 原始程式碼管理外掛程式可以有自己的 UI,該 UI 可能由圖中的兩個部分組成。 標記為「供應商 UI」的框表示您作為原始程式碼管理外掛程式建立者提供的自訂使用者介面元素。 當使用者調用進階原始程式碼管理操作時,原始程式碼管理外掛程式會直接顯示這些操作。 標記為"説明者 UI"的框是一組透過 IDE 間接調用的原始程式碼管理外掛程式 UI 功能。 原始程式碼管理外掛程式透過 IDE 提供的特殊回檔功能將與 UI 相關的消息傳遞給 IDE。 説明程式 UI 有助於與 IDE 進行更無縫的整合(通常使用**進階**按鈕),從而提供更統一的最終用戶體驗。

 原始程式碼管理外掛程式[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]不能對 shell 進行更改,因此無法更改原始碼管理配接器包或 IDE 提供的原始碼管理 UI。 它必須最大限度地利用通過實現各種原始程式碼管理外掛程式 API 功能提供的靈活性,這些功能有助於最終用戶獲得整合體驗。 原始程式碼管理外掛程式 API 文件的參考部分包括某些進階原始程式碼管理外掛程式功能的資訊。 要利用這些功能,原始程式碼管理外掛程式必須在初始化期間將其進階功能聲明給 IDE,並且必須為每個功能實現特定的進階功能。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)
- [詞彙](../../extensibility/source-control-plug-in-glossary.md)
- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)
