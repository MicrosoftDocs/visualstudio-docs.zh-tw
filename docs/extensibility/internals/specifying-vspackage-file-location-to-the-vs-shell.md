---
title: 指定 VS Shell VSPackage 的檔案位置 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7a4270fbd723e6c5aa6f16066066e0ca4ac74e5d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>VS Shell 指定 VSPackage 的檔案位置
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 必須是能夠找出組件載入 VSPackage 的 DLL。 您可以找出它以各種方式下, 表中所述。  
  
|方法|描述|  
|------------|-----------------|  
|使用程式碼基底登錄機碼。|程式碼基底的索引鍵可以用來直接[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]從任何完整的檔案路徑載入 VSPackage 組件。 索引鍵的值應該是 DLL 的檔案路徑。 這是最佳的方式有[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]將封裝組件載入。 這項技術有時稱為 「 程式碼基底/私密金鑰安裝目錄技術。 」 在註冊期間的程式碼基底值透過傳遞至註冊屬性類別的執行個體<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext>型別。|  
|將放入 DLL **PrivateAssemblies**目錄。|將組件中的**PrivateAssemblies**子目錄[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]目錄。 組件位於**PrivateAssemblies**會自動偵測，但不是會顯示在**加入參考** 對話方塊。 之間的差異**PrivateAssemblies**和**PublicAssemblies**是組件中**PublicAssemblies**會列舉在**加入參考**  對話方塊。 如果您選擇不使用 「 程式碼基底/私密金鑰安裝目錄 」 的技術，則您應安裝到**PrivateAssemblies**目錄。|  
|使用強式名稱組件和組件登錄機碼。|組件金鑰可用來明確地直接[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]載入強式命名 VSPackage 組件。 索引鍵的值應該是強式名稱組件。|  
|將放入 DLL **PublicAssemblies**目錄。|最後，組件也可置於**PublicAssemblies**子目錄。 組件位於**PublicAssemblies**會自動偵測和也會出現在**加入參考** 對話方塊中的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。<br /><br /> VSPackage 組件只應該放在**PublicAssemblies**目錄，如果它們包含受管理的要由其他 VSPackage 開發人員可重複使用的元件。 大部分的組件不符合此準則。|  
  
> [!NOTE]
>  所有相依組件使用強式名稱、 帶正負號的組件。 這些組件也應該安裝在您的目錄或全域組件快取 (GAC) 中。 這可防止與具有相同的基底檔案名稱，又稱為弱式名稱繫結的組件發生衝突。