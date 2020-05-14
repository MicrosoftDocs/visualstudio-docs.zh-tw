---
title: 何時建立項目型態 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 861250dac25288f353cbd5c57f510bf67dadce70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703436"
---
# <a name="when-to-create-project-types"></a>建立專案類型的時機
創建新項目類型為使用者自定義[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供了基礎。 但是,並非所有自定義項都需要[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]創建新的項目類型。 以下指南將説明您確定方案是否需要新的項目類型。

## <a name="create-a-new-project-type"></a>建立新項目型態
 如果要自訂[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]以以下一種或多種方式操作,則必須建立項目類型:

- 參與生成、部署、配置和原始程式碼管理。

- 提供調試支援。

- 在**解決方案資源管理員**中顯示專案項。

- 使用 **「打開項目**」或 **「新專案」** 對話方塊。

- 支援專案嵌套。

## <a name="extend-an-existing-project-type"></a>延伸現有項目型態
 您可能希望建立新的項目類型,該類型可透過以下方式修改[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]或擴展現有項目類型的行為,例如,[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]修改專案的生成過程:

- 將多個檔用作單個單元。

- 將單個文件顯示為子項的層次結構。

- 在編輯器周圍顯示命令上下文。

- 顯示編輯器的服務上下文。

## <a name="use-an-existing-project-type"></a>使用現有項目型態
 有時不需要創建新專案。 下表顯示了不必為其創建項目類型的任務。

|Task|描述|
|----------|-----------------|
|處理命令|任何 VS 套件都可以處理命令。|
|編譯編輯器|可以註冊自定義編輯器。 關於詳細資訊,請參考[文件視窗與編輯器](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)。|
|擁有視窗|您可以建立工具和文件視窗,而無需添加新的項目類型。|
|在「屬性」視窗中公開屬性|所有物件都可以公開屬性。|

## <a name="create-a-project-subtype"></a>建立項目子型態
 可以使用專案子類型擴展託管項目類型,而無需創建新的項目類型。 專案子類型使用 COM 聚合來擴展在[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)][!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]Microsoft 或 中編寫的託管專案。 使用 COM 聚合,您可以重用大部分託管專案系統實現,並且仍然通過聚合和使用支援介面對特定方案進行自定義。 有關項目子型態的詳細資訊,請參考[專案子型態](../../extensibility/internals/project-subtypes.md)。

## <a name="see-also"></a>另請參閱
- [文件視窗與編輯器](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [檢查清單︰建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)
