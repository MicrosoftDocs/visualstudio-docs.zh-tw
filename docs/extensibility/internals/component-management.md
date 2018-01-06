---
title: "元件管理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 398986499732a36819808b07f05f7d6b46787a94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="component-management"></a>管理元件
Windows 安裝程式中的工作單位被指 Windows 安裝程式元件 （有時稱為 WICs 或只是元件）。 GUID 識別每個 WIC，也就是安裝和參考計數，若是使用 Windows Installer 的設定的基本單位。  
  
 雖然您可以使用數個產品建立 VSPackage installer，此討論假設您使用的 Windows Installer (.msi) 檔案。 在建立您的安裝程式時，您必須正確地管理檔案部署，這樣可以隨時都能正確的參考計數執行。 因此，您產品的不同版本將不會干擾或中斷彼此中混合的安裝和解除安裝案例。  
  
 在 Windows 安裝程式中，參考計數，就會發生在元件層級。 您必須仔細組織資源 — 檔案、 登錄項目，以及其他 — 元件。 有其他層級的組織 — 例如模組、 功能和產品，可協助在不同情況下。 如需詳細資訊，請參閱[Windows 安裝程式的基本概念](../../extensibility/internals/windows-installer-basics.md)。  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>撰寫-並存安裝的安裝程式的指導方針  
  
-   作者的檔案和登錄機碼他們自己的元件版本之間共用。  
  
     這可讓您輕鬆使用它們在下一版。 例如，全域註冊類型程式庫檔案延伸模組，登錄 HKEY_CLASSES_ROOT，等其他項目。  
  
-   共用的元件群組到個別的合併模組。  
  
     這可協助您撰寫正確的並存向前移動。  
  
-   跨版本使用相同的 Windows Installer 元件安裝共用的檔案和登錄機碼。  
  
     如果您使用不同的元件時，檔案和登錄項目會解除安裝時解除安裝一個已建立版本的 VSPackage，但仍安裝另一個 VSPackage。  
  
-   請勿混合版本設定和共用同一個元件中的項目。  
  
     如此一來，因此無法安裝共用的項目至全域位置和版本設定隔離的位置的項目。  
  
-   沒有指向已建立版本的檔案共用的登錄機碼。  
  
     如果您這樣做，共用的金鑰會覆寫已安裝另一個版本的 VSPackage。 第二個版本中移除之後，索引鍵指向的檔案會消失。  
  
## <a name="see-also"></a>請參閱  
 [選擇 共用和版本建立 Vspackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage 安裝案例](../../extensibility/internals/vspackage-setup-scenarios.md)