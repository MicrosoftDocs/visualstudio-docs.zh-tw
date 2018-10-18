---
title: VSPackage 狀態 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: douge
ms.openlocfilehash: 1fee544dcf9bec9295d297f153df7f86dd464bda
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192851"
---
# <a name="vspackage-state"></a>VSPackage 狀態
許多因素會決定一組持續性的值或狀態的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]應用程式。  
  
-   專案沒有專案和設定的屬性。  
  
-   解決方案會有的屬性。  
  
-   使用者設定會決定的大小和位置的文件視窗中，工具視窗、 停駐狀態和鍵盤快速鍵。  
  
-   應用程式可以有使用者設定的選項。  
  
-   應用程式建立的物件可以有自己的屬性。  
  
 以下是幾種，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]可以管理應用程式狀態：  
  
-   透過專案和方案屬性頁。  
  
-   透過**匯入和匯出設定精靈**，這可讓使用者將設定移到另一部電腦。  
  
-   透過**選項** 對話方塊中，其中包含與應用程式相關的選項。  
  
-   透過**屬性**視窗中，它會公開物件的屬性。  
  
-   透過自動化。 應用程式可以存取已公開至自動化的 VSPackage 和物件的屬性。  
  
 基礎應用程式的狀態是各種持續性機制，可啟用儲存和還原應用程式狀態。  
  
## <a name="in-this-section"></a>本節內容  
 [狀態持續性支援](../misc/support-for-state-persistence.md)  
 列出用於儲存和還原 VSPackage 以及重設 VSPackage 狀態的常見策略。  
  
 [選項和選項頁](../extensibility/internals/options-and-options-pages.md)  
 導入了一般和自訂的 [選項] 頁面，並說明如何實作它們。  
  
 [建立選項頁](../extensibility/creating-an-options-page.md)  
 說明如何建立兩個 [選項] 頁面、 簡單的頁面和自訂的頁面。  
  
 [設定類別的支援](../misc/support-for-settings-categories.md)  
 使用者設定和如何建立和保存這些討論。  
  
 [建立設定分類](../extensibility/creating-a-settings-category.md)  
 說明如何建立[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]設定類別，並用來儲存值，並還原從設定檔的值。  
  
 [擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)  
 說明如何顯示和變更的值中的物件**屬性**視窗。  
  
 [將屬性公開至屬性視窗](../extensibility/exposing-properties-to-the-properties-window.md)  
 說明如何將物件的公用屬性公開**屬性**視窗。  
  
 [支援專案和組態屬性](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 說明如何顯示及變更專案和設定的屬性。  
  
 [取得專案屬性](../extensibility/getting-project-properties.md)  
 引導您完成建立 managed 的 VSPackage 的工具視窗中顯示專案內容的步驟。  
  
 [使用設定存放區](../extensibility/using-the-settings-store.md)  
 說明的設定存放區持續性機制，以及如何使用它。  
  
## <a name="related-sections"></a>相關章節  
 [VSPackage](../extensibility/internals/vspackages.md)  
 提供一般的方向，這些主題說明如何建立和使用 Vspackage。