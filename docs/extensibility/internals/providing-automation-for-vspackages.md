---
title: 為 VS 套件提供自動化 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6364f9cbaf3409e076eeb77365e5d793c7be96cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705955"
---
# <a name="providing-automation-for-vspackages"></a>為 VSPackage 提供自動化
提供 VSPackage 自動化的兩種主要方法:通過實現特定於 VSPackage 的物件和實現標準自動化物件。 通常,這些用於擴展環境的自動化模型。

## <a name="vspackage-specific-objects"></a>VS 套件指定物件
 自動化模型中的某些位置要求您提供 VSPackage 獨有的自動化物件。 例如,新專案需要僅提供 VSPackage 的不同物件。 這些物件的名稱在註冊表中輸入,並通過對環境`DTE`物件的調用獲得。

 當自動化消費者使用透過標準物件的Object 屬性提供的物件時,也可以獲取特定於 VSPackage 的物件。 例如,標準`Window`物件具有一`Object`個 屬性,通常稱為`Windows.Object`屬性。 當消費者調用`Window.Object`VSPackage 中實現的視窗時,將傳遞自己設計的特定自動化物件。

#### <a name="projects"></a>專案
 VSPackage 可以通過自己的 VSPackage 特定物件擴展新項目類型的自動化模型。 為 VSPackage 提供新的自動化物件的主要目的是將<xref:Microsoft.VisualStudio.VCProjectEngine.VCProject><xref:VSLangProj80.VSProject2>唯一 專案物件與 物件區分開來。 當您希望提供一種從其他項目類型中並排顯示的專案類型以外的單一或反覆運算專案類型的方法時,這種差別化是很方便的。 有關詳細資訊,請參閱[公開項目物件](../../extensibility/internals/exposing-project-objects.md)。

#### <a name="events"></a>事件
 環境的事件體系結構為您提供了另一個位置來追加自己的 VSPackage 特定物件。 例如,通過創建自己的唯一事件物件,可以擴展環境的事件模型。 當新專案添加到您自己的項目類型時,您可能希望提供您自己的事件。 有關詳細資訊,請參閱[公開事件](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)。

#### <a name="window-objects"></a>視窗物件
 Windows 可以在調用時將特定於 VSPackage 的自動化物件傳回環境。 實現派生自<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>的<xref:EnvDTE.IExtensibleObject>物件`IDispatch`或 該回手屬性,擴展其駐點的視窗物件。 例如,可以使用此方法為視窗框架中設置的控制項提供自動化。 此物件及其可能擴展的任何其他對象的語義是您設計的。 有關詳細資訊,請參閱[如何:為 Windows 提供自動化](../../extensibility/internals/how-to-provide-automation-for-windows.md)。

#### <a name="options-pages-on-the-tools-menu"></a>「工具」選單上的選項頁面
 您可以通過實現頁面和向註冊表添加資訊來創建頁面來擴展工具、選項自動化模型,以創建您自己的選項。 然後,可以通過環境物件模型與任何其他選項頁一樣調用您的頁面。 如果透過 VSPackages 添加到環境的功能的設計需要選項頁,則還應添加自動化支援。 關於詳細資訊,請參閱[選項頁的自動化支援](../../extensibility/internals/automation-support-for-options-pages.md)。

## <a name="standard-automation-objects"></a>標準自動化物件
 要擴展專案的自動化,您還可以實現標準自動化物件(派生自`IDispatch`),該物件位於其他專案物件旁邊,並實現標準方法和屬性。 標準物件`Projects`的範例包括插入到解決方案層次結構(如`Project`、`ProjectItem``ProjectItems`和) 的專案物件。 每個新項目類型都應實現這些物件(可能還有其他物件,具體取決於專案的語義)。

 從某種意義上說,這些物件提供了 VSPackage 特定專案物件的相反優勢。 標準自動化物件允許以通用方式使用專案,就像支援相同物件的任何其他項目一樣。 因此,針對常規`Project`和`ProjectItem`物件編寫的外接程式可以針對任何類型的專案運行。 有關詳細資訊,請參閱[專案建模](../../extensibility/internals/project-modeling.md)。
