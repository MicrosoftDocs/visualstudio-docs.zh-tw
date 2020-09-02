---
title: VSPackage 狀態 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: jillfra
ms.openlocfilehash: f3140b527673f87b1d7c552e99584232494aed7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62979991"
---
# <a name="vspackage-state"></a>VSPackage 狀態
許多因素會決定應用程式的保存值（或狀態）集合 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
- 專案具有專案和設定屬性。  
  
- 解決方案具有屬性。  
  
- 使用者設定決定文件視窗、工具視窗、停駐狀態和鍵盤快速鍵的大小與位置。  
  
- 應用程式可以有使用者所設定的選項。  
  
- 應用程式所建立的物件可以有自己的屬性。  
  
  以下是 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 可以管理應用程式狀態的一些方式：  
  
- 透過 [專案] 和 [方案屬性頁]。  
  
- 透過 [匯 **入和匯出設定] 嚮導**，讓使用者可以將設定從一部電腦移到另一部電腦。  
  
- 透過 [ **選項** ] 對話方塊，其中包含與應用程式相關的選項。  
  
- 在 [ **屬性** ] 視窗中，它會公開物件的屬性。  
  
- 透過 Automation。 應用程式可以存取已公開給 Automation 的 VSPackage 和物件屬性。  
  
  應用程式狀態的基礎是各種持續性機制，可讓您儲存及還原應用程式狀態。  
  
## <a name="in-this-section"></a>本節內容  
 [狀態持續性支援](../misc/support-for-state-persistence.md)  
 列出用於儲存和還原 VSPackage 以及重設 VSPackage 狀態的常見策略。  
  
 [選項和選項頁](../extensibility/internals/options-and-options-pages.md)  
 介紹一般和自訂選項頁面，並說明如何執行這些頁面。  
  
 [建立選項頁](../extensibility/creating-an-options-page.md)  
 說明如何建立兩個選項頁面、簡單的頁面和自訂頁面。  
  
 [設定類別的支援](../misc/support-for-settings-categories.md)  
 討論使用者設定以及這些設定的建立與保存方式。  
  
 [建立設定分類](../extensibility/creating-a-settings-category.md)  
 說明如何建立 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 設定類別，並使用它來儲存值，並從配置檔案還原值。  
  
 [擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)  
 說明如何在 [ **屬性** ] 視窗中顯示和變更物件的值。  
  
 [將屬性公開至屬性視窗](../extensibility/exposing-properties-to-the-properties-window.md)  
 說明如何將物件的公用屬性公開至 [ **屬性** ] 視窗。  
  
 [支援專案和組態屬性](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 說明如何顯示及變更專案和設定屬性。  
  
 [取得專案屬性](../extensibility/getting-project-properties.md)  
 引導您完成建立在工具視窗中顯示專案屬性之 managed VSPackage 的步驟。  
  
 [使用設定存放區](../extensibility/using-the-settings-store.md)  
 說明設定存放區持續性機制，以及如何使用。  
  
## <a name="related-sections"></a>相關章節  
 [VSPackages](../extensibility/internals/vspackages.md)  
 提供主題的一般方向，說明如何建立和使用 Vspackage。