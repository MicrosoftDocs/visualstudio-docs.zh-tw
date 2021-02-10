---
title: 執行原始檔控制的時機 VSPackage
description: 瞭解可用於擴充 Visual Studio 原始檔控制解決方案的原始檔控制外掛程式和原始檔控制 Vspackage 的選項。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 80c86a8ab40b74d1b8f2838e3bf4359af41b0fc5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963428"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>判斷是否要執行原始檔控制 VSPackage

本節介紹原始檔控制外掛程式的選項，以及用於擴充原始檔控制解決方案的原始檔控制 Vspackage，並提供有關選擇適當整合路徑的廣泛指導方針。

## <a name="small-source-control-solution-with-limited-resources"></a>資源有限的小型原始檔控制解決方案

 如果您的資源有限，而且無法負擔撰寫原始檔控制封裝的額外負荷，您可以建立原始檔控制外掛程式 API 型外掛程式。這樣做可讓您與原始檔控制封裝並存運作，而且您可以視需要在原始檔控制外掛程式和套件之間切換。 如需詳細資訊，請參閱 [註冊和選取](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)。

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>具有豐富功能集的大型原始檔控制解決方案

 如果您想要執行原始檔控制解決方案，以提供不使用原始檔控制外掛程式 API 來充分捕捉的豐富原始檔控制模型，您可以將原始檔控制封裝視為整合路徑。 這特別適用于您想要取代原始檔控制介面卡封裝 (它會與原始檔控制外掛程式進行通訊，並提供基本的原始檔控制 UI) ，讓您能夠以自訂的方式處理原始檔控制事件。 如果您已經有令人滿意的原始檔控制 UI，而且想要在中保留該體驗 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，則原始檔控制封裝選項可讓您這樣做。 原始檔控制封裝不是泛型的，而且是專為搭配 IDE 使用而設計 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

 如果您想要執行原始檔控制解決方案，以提供對原始檔控制邏輯和 UI 的彈性和更豐富的控制，您可能會想要使用原始檔控制封裝整合路由。 您可以：

1. 註冊您自己的原始檔控制 VSPackage (查看 [註冊和選取](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)) 。

2. 以您的自訂 UI 取代預設的原始檔控制 UI (查看 [自訂使用者介面](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)) 。

3. 指定要使用的字元，並處理方案總管圖像事件 (請參閱圖像 [控制](../../extensibility/internals/glyph-control-source-control-vspackage.md)) 。

4. 處理查詢編輯和查詢儲存事件 (查看 [查詢編輯查詢儲存](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)) 。

## <a name="see-also"></a>另請參閱

- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)
