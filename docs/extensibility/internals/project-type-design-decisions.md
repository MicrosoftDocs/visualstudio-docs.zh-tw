---
title: 項目類型設計決策 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e33ac1c4168593b881f799dfdfb94005fb55fc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706365"
---
# <a name="project-type-design-decisions"></a>專案類型的設計決策
在創建新項目類型之前,必須就專案類型做出多個設計決策。 您必須決定專案將包含哪些類型的專案、如何保留專案檔以及您將使用的承諾模型。

## <a name="project-items"></a>專案項目
 您的專案是否使用檔案或抽象物件? 如果使用檔案,這些檔案是基於引用還是基於目錄的檔? 檔或抽象對像是本地還是遠端?

 專案中的專案可以是檔,也可以是更抽象的物件,如資料庫存儲庫中的物件或 Internet 上的數據連接。 如果專案是檔,則專案可以是基於引用的專案,也可以是基於目錄的專案。

 在基於引用的專案中,項可以出現在多個專案中。 但是,項表示的實際檔僅位於一個目錄中。 在基於目錄的專案中,目錄結構中存在所有專案項。

 本地專案存儲在安裝應用程式的同一台電腦上。 遠端專案可以儲存在本地網路中的單獨伺服器上,也可以存儲在 Internet 的其他地方。

## <a name="project-file-persistence"></a>專案檔持久性
 資料是存儲在通用平面文件系統中還是存儲在結構化存儲中? 檔案是使用標準編輯器還是特定於專案的編輯器打開?

 要保留其數據,大多數應用程式將其數據保存在檔中,然後在使用者必須查看或更改資訊時將其讀取。

 當多個元件物件模型 (COM) 物件需要將其持久化數據儲存在單個檔中時,通常使用結構化存儲(也稱為複合檔案)。 使用結構化存儲,多個不同的軟體元件可以共用單個磁碟檔。

 對於專案中專案的持久性,需要考慮多個選項。 您可以執行以下任一選項:

- 更改後單獨保存每個檔。

- 在單個 **「保存」** 操作中捕獲多個事務。

- 在本地保存檔,然後發佈到伺服器,或者當專案表示與遠端物件的數據連接時,使用另一種方法保存專案項。

  有關持久性的詳細資訊,請參閱[專案持久性](../../extensibility/internals/project-persistence.md)以及[開啟和儲存項目項目](../../extensibility/internals/opening-and-saving-project-items.md)。

## <a name="project-commitment-model"></a>專案承諾模型
 持久化數據物件是否會在直接模式或交易模式下打開?

 當直接模式打開數據物件時,將立即合併對數據所做的更改,或者當使用者手動保存檔時。

 使用事務模式打開數據物件時,更改將保存到記憶體中的臨時位置,直到使用者手動選擇保存檔之前不會提交更改。 此時,所有更改必須同時發生,否則不會進行任何更改。

## <a name="see-also"></a>另請參閱
- [檢查清單︰建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)
- [專案持續性](../../extensibility/internals/project-persistence.md)
- [專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md)
- [專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)
- [建立專案類型](../../extensibility/internals/creating-project-types.md)
