---
title: 建立專案類型的時機 |Microsoft Docs
description: 瞭解如何判斷自訂使用者的 Visual Studio 是否需要新的專案類型。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 458ca77ebcd8017b9834a8925edec255ca04cc13
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487825"
---
# <a name="when-to-create-project-types"></a>建立專案類型的時機
建立新的專案類型可為使用者提供自訂的基礎 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 但是，並非所有自訂都需要建立新的專案類型 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 下列指導方針可協助您判斷您的案例是否需要新的專案類型。

## <a name="create-a-new-project-type"></a>建立新的專案類型
 如果您想要自訂 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 以下列一或多種方式執行動作，您必須建立專案類型：

- 參與組建、部署、設定和原始檔控制。

- 提供調試支援。

- 顯示 **方案總管** 中的專案專案。

- 使用 [ **開啟專案** ] 或 [ **新增專案** ] 對話方塊。

- 支援專案嵌套。

## <a name="extend-an-existing-project-type"></a>擴充現有的專案類型
 您可能會想要建立新的專案類型，以利用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 下列方式來修改或擴充現有專案類型的行為，例如，修改專案的組建流程 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ：

- 以單一單位使用多個檔案。

- 將單一檔案顯示為子專案的階層。

- 在編輯器周圍顯示命令內容。

- 顯示編輯器的服務內容。

## <a name="use-an-existing-project-type"></a>使用現有的專案類型
 有時不需要建立新專案。 下表顯示您不需要為其建立專案類型的工作。

|Task|描述|
|----------|-----------------|
|處理命令|任何 VSPackage 都可以處理命令。|
|建立編輯器|您可以註冊自訂編輯器。 如需詳細資訊，請參閱 [檔視窗和編輯器](/previous-versions/bb165691(v=vs.100))。|
|擁有視窗|您可以建立工具和文件視窗，而不需要加入新的專案類型。|
|公開屬性視窗中的屬性|所有物件都可以公開屬性。|

## <a name="create-a-project-subtype"></a>建立專案子類型
 您可以使用專案子類型來擴充 managed 專案類型，而不需要建立新的專案類型。 專案子類型使用 COM 匯總來擴充以 Microsoft 或撰寫的 managed 專案 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 。 使用 COM 匯總，您可以重複使用大部分的 managed 專案系統，並且仍可透過匯總和使用支援介面來自訂特定案例。 如需專案子類型的詳細資訊，請參閱 [專案子類型](../../extensibility/internals/project-subtypes.md)。

## <a name="see-also"></a>另請參閱
- [檔視窗和編輯器](/previous-versions/bb165691(v=vs.100))
- [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)