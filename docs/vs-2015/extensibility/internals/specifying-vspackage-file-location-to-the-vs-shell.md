---
title: 指定 VSPackage 檔案位置，為 VS Shell |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d7abb72d3d577c4870030c76f87f0a41f133480
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940035"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>為 VS Shell 指定 VSPackage 檔案位置
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 必須是找不到組件載入 VSPackage 的 DLL。 您可以找到以各種方式下, 表中所述。  
  
|方法|描述|  
|------------|-----------------|  
|使用程式碼基底登錄機碼。|程式碼基底的索引鍵可用來直接[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]從任何完整的檔案路徑載入 VSPackage 組件。 索引鍵的值應該是 DLL 的檔案路徑。 這是最佳的方式有[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]載入您的封裝組件。 這項技術有時稱為 「 程式碼基底/私密金鑰安裝目錄技術。 」 在註冊期間的程式碼基底值透過傳遞至註冊屬性類別的執行個體<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext>型別。|  
|將放入 DLL **PrivateAssemblies**目錄。|在組件放**PrivateAssemblies**子目錄[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]目錄。 組件位於**PrivateAssemblies**會自動偵測，但不是會顯示於**新增參考** 對話方塊。 之間的差異**PrivateAssemblies**並**PublicAssemblies**是組件中**PublicAssemblies**會列舉在**加入參考**  對話方塊。 如果您選擇不使用 「 程式碼基底/私密金鑰安裝目錄 」 的技巧，則您應該將它安裝到**PrivateAssemblies**目錄。|  
|使用強式名稱組件和組件登錄機碼。|組件金鑰可用來明確地直接[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]載入強式命名為 VSPackage 組件。 索引鍵的值應該是組件的強式名稱。|  
|將放入 DLL **PublicAssemblies**目錄。|最後，組件也可以放入**PublicAssemblies**子目錄。 組件位於**PublicAssemblies**會自動偵測，並也會出現在**的 [加入參考**] 對話方塊中的[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。<br /><br /> VSPackage 組件應該只能置於**PublicAssemblies**如果它們包含的目錄管理是由其他 VSPackage 開發人員重複使用的元件。 大部分的組件不符合此準則。|  
  
> [!NOTE]
>  使用強式名稱的所有相依組件已簽署組件。 這些組件也應該安裝在您自己的目錄或全域組件快取 (GAC) 中。 這可防止使用具有相同的基底檔案名稱，稱為弱式名稱繫結的組件的衝突。
