---
title: 建立專案類型的時機 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff29843965c220c505266a9cd973e5695c0b9dab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721558"
---
# <a name="when-to-create-project-types"></a>建立專案類型的時機
建立新的專案類型，可提供自訂使用者 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的基礎。 不過，並非所有的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 自訂都需要建立新的專案類型。 下列指導方針可協助您判斷您的案例是否需要新的專案類型。

## <a name="create-a-new-project-type"></a>建立新的專案類型
 如果您想要自訂 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 來採取下列一或多種方式，則必須建立專案類型：

- 參與組建、部署、設定和原始檔控制。

- 提供調試支援。

- 在**方案總管**中顯示專案專案。

- 使用 [**開啟專案**] 或 [**新增專案**] 對話方塊。

- 支援專案的嵌套。

## <a name="extend-an-existing-project-type"></a>擴充現有的專案類型
 您可能想要建立新的專案類型，以下列方式使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 來修改或擴充現有專案類型的行為，例如，修改 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 專案的組建進程：

- 使用多個檔案做為單一單位。

- 將單一檔案顯示為子專案的階層。

- 在編輯器周圍顯示命令內容。

- 顯示編輯器的服務內容。

## <a name="use-an-existing-project-type"></a>使用現有的專案類型
 有時不需要建立新的專案。 下表顯示您不需要為建立專案類型的工作。

|工作|描述|
|----------|-----------------|
|處理命令|任何 VSPackage 都可以處理命令。|
|建立編輯器|您可以註冊自訂編輯器。 如需詳細資訊，請參閱[文件視窗和編輯器](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)。|
|擁有視窗|您可以建立工具和文件視窗，而不需要加入新的專案類型。|
|公開屬性視窗中的屬性|所有物件都可以公開屬性。|

## <a name="create-a-project-subtype"></a>建立專案子類型
 您可以使用專案子類型來擴充 managed 專案類型，而不需要建立新的專案類型。 專案子類型：使用 COM 匯總來擴充以 Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 撰寫的 managed 專案。 有了 COM 匯總，您可以重複使用大部分的受控專案系統實作為，並透過匯總和支援介面的使用，針對特定案例進行自訂。 如需專案子類型的詳細資訊，請參閱[專案子類型](../../extensibility/internals/project-subtypes.md)。

## <a name="see-also"></a>請參閱
- [文件視窗和編輯器](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [檢查清單︰建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)