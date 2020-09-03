---
title: 專案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 44
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a251af12ccf4be5f0f48f789ac59fedaed3299b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183941"
---
# <a name="projects"></a>專案
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在 Visual Studio 中，專案是開發人員用來組織原始程式碼檔的容器，以及顯示在 **方案總管**中的其他資源。 專案通常是檔案 (例如，c #) 專案的 .csproj 檔案，會儲存原始程式碼檔和點陣圖檔案等資源的參考。 專案可讓您組織、建立、偵測和部署原始程式碼、Web 服務和資料庫的參考，以及其他資源。 Vspackage 可透過三種主要方式擴充 Visual Studio 專案系統： *專案類型*、 *專案子類型*和 *自訂工具*。  
  
## <a name="in-this-section"></a>本節內容  
 [專案類型](../../extensibility/internals/project-types.md)  
 *專案類型* 可新增對新專案類型的支援，例如程式設計語言。 例如，Visual Studio 支援的每一種語言都有自己的專案類型，而 IronPython 整合範例則包含 IronPython 語言的專案類型。 您必須為 c # 或 Visual Basic 以外的語言建立專案類型，以自訂在 **方案總管**中建立、調試、部署和顯示專案的方式。 如需詳細資訊，請參閱 [專案類型](../../extensibility/internals/project-types.md)。  
  
 [專案子類型](../../extensibility/internals/project-subtypes.md)  
 *專案子類型* 是以專案類型為基礎，而且可以用來自訂建立、調試和部署專案的方式。 Visual Studio 搭配智慧型裝置專案使用專案子類型;他們自訂部署，方法是將新建立的程式從開發電腦複製到目標裝置。 C # 和 Visual Basic 專案類型可以用來作為專案子類型的基礎;C + + 專案類型不能。 您自己的專案類型也可以用來做為專案子類型的基礎。 如需詳細資訊，請參閱 [專案子類型](../../extensibility/internals/project-subtypes.md)。  
  
 [Web 專案](../../extensibility/internals/web-projects.md)  
 說明 Web 專案，接著建立 Web 應用程式。  
  
 [新專案產生：在幕後，第一](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) 篇和 [新專案產生：在幕後，第二部分](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 說明當您建立新專案時實際發生的情況。  
  
 [VSSDK 範例](../../misc/vssdk-samples.md)  
 描述 VSSDK 中處理專案和方案的範例。  
  
## <a name="related-sections"></a>相關章節  
 [深入探索 Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 說明 Visual Studio 延伸的不同層面。
