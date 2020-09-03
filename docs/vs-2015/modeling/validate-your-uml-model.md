---
title: 驗證您的 UML 模型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, constraints
- UML, validation
ms.assetid: deed5092-c11d-4431-a801-1e866a103075
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8dfaf19e358d96b7737b06880d6fa4581b5c54f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659377"
---
# <a name="validate-your-uml-model"></a>驗證 UML 模型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在 Visual Studio 中繪製的一些 UML 模型可能會在您的專案中被視為無效。 例如，您可能需要使用案例一律必須連結到具有生命線的循序圖，而生命線代表使用案例的執行者。 您可以安裝或定義 *條件約束* ，協助您的小組符合這類需求。 當使用者儲存或開啟模型時，可以套用條件約束，也可以用功能表命令來叫用條件約束。

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 沒有提供條件約束，因為它們取決於您的小組如何解譯和使用 UML 模型。 但是，您可以定義自己的條件約束，以及安裝其他使用者所定義的條件約束。 若要瞭解如何定義條件約束，並封裝它們來散發，請參閱 [定義 UML 模型的驗證條件約束](../modeling/define-validation-constraints-for-uml-models.md)。

## <a name="invoking-validation"></a>叫用驗證
 當您已安裝驗證延伸模組時，它提供的條件約束可能會套用在下列情況。 某些條件約束已設定為只在這些部分情況下套用。

- **驗證命令。** 若要在任何時間叫用驗證，請按一下 [**架構**] 功能表上的 [**驗證 UML 模型**]。

  > [!NOTE]
  > 已安裝驗證條件約束時，才會出現命令。

- **儲存模型時。** 當您儲存模型時，可以套用驗證條件約束。 這些條件約束的目的是協助確定您不會儲存根據專案解譯無效的模型。

   如果發生錯誤，會詢問您是否仍要儲存模型。 您可以選擇要更正錯誤，還是依舊儲存模型。

- **開啟模型時。** 當您開啟模型時，可以套用驗證方法以還原在您儲存模型時已存在的錯誤訊息。 處理模型不同部分的使用者所做的變更不一致時，也可能引入錯誤。 如需詳細資訊，請參閱 [共用模型和匯出圖表](../modeling/share-models-and-exporting-diagrams.md)。

  驗證錯誤會在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 錯誤視窗中報告。

  若要在圖表中選取不正確的項目，請按兩下錯誤。 這只有在不正確的項目會顯示在已開啟的圖表時才能使用。

## <a name="installing-validation-constraints"></a>安裝驗證條件約束
 條件約束封裝在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 擴充功能 (VSIX) 檔案內。 通常，一組條件約束會是同時包含其他定義 (例如功能表命令、設定檔和工具箱項目) 的擴充功能的一部分。

#### <a name="to-install-a-visual-studio-extension"></a>安裝 Visual Studio 擴充功能

1. 按兩下 Windows 檔案總管 (中的 **.vsix** 檔，或檔案總管) 。

2. 重新啟動已在執行的任何 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 執行個體。

## <a name="disabling-and-uninstalling-validation-constraints"></a>停用並解除安裝驗證條件約束
 當您想要使用條件約束並不適用的模型時，可以暫時停用包含它們的擴充功能。 如此一來，您可以藉由啟用和停用不同的擴充功能，在不同的時間使用不同種類的模型。

#### <a name="to-disable-or-uninstall-a-visual-studio-extension"></a>停用或解除安裝 Visual Studio 擴充功能

1. 按一下 [ [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **工具** ] 功能表上的 [ **擴充功能和更新**]。

2. 在擴充功能旁，按一下 [ **停** 用] 以暫時停用擴充功能。 您可以在稍後返回 [ **擴充功能和更新** ] 視窗重新啟用它。

     \- 或 -

     按一下 [ **卸載** ] 以移除擴充功能。

3. 重新啟動 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。

## <a name="see-also"></a>另請參閱
 [定義 UML 模型的驗證條件約束為](../modeling/define-validation-constraints-for-uml-models.md)[您的應用程式建立模型](../modeling/create-models-for-your-app.md)[在開發過程中使用模型](../modeling/use-models-in-your-development-process.md)
