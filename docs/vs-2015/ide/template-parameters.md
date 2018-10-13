---
title: 範本參數 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ef4e1a6e3c56df744ce5375a1cb3a1dbd53a6fad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238897"
---
# <a name="template-parameters"></a>範本參數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

透過使用範本中的參數，您可以在範本具現化時取代範本機碼部分的值，例如類別名稱和命名空間。 當使用者按一下 [新增專案] 或 [新增項目] 對話方塊中的 [確定] 時，在背景執行的範本精靈即會取代這些參數。  
  
## <a name="declaring-and-enabling-template-parameters"></a>宣告和啟用範本參數  
 範本參數是以 $*parameter*$ 格式來宣告。 例如:   
  
-   $safeprojectname$  
  
-   $guid1$  
  
-   $guid5$  
  
#### <a name="to-enable-parameter-substitution-in-templates"></a>若要啟用範本中的參數替換  
  
1.  在範本的 .vstemplate 檔案中，找出對應至您要為其啟用參數取代之項目的 `ProjectItem` 項目。  
  
2.  將 `ReplaceParameters` 項目的 `ProjectItem` 屬性設定為 `true`。  
  
3.  在適當時，於專案項目的程式碼檔案中納入參數。 例如，下列參數指定用於檔案中命名空間的安全專案名稱：  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
## <a name="reserved-template-parameters"></a>保留的範本參數  
 下表列出可用於任何範本的保留範本參數。  
  
> [!NOTE]
>  範本參數會區分大小寫。  
  
|參數|描述|  
|---------------|-----------------|  
|`clrversion`|通用語言執行平台 (CLR) 的最新版本。|  
|`GUID [1-10]`|GUID；用來取代專案檔中的專案 GUID。 您最多可以指定 10 個唯一的 GUID (例如，`guid1)`。|  
|`itemname`|使用者在 [新增項目] 對話方塊中所提供的名稱。|  
|`machinename`|目前的電腦名稱 (例如，Computer01)。|  
|`projectname`|使用者在 [新增專案] 對話方塊中所提供的名稱。|  
|`registeredorganization`|來自 HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization 的登錄機碼值。|  
|`rootnamespace`|目前專案的根命名空間。 這個參數只適用於項目範本。|  
|`safeitemname`|使用者在 [新增項目] 對話方塊中所提供的名稱，其中已將所有 Unsafe 字元和空格移除。|  
|`safeprojectname`|使用者在 [新增專案] 對話方塊中所提供的名稱，其中已將所有 Unsafe 字元和空格移除。|  
|`time`|目前的時間，格式為 DD/MM/YYYY 00:00:00。|  
|`SpecificSolutionName`|方案名稱。 若已核取 [建立方案目錄]，則 `SpecificSolutionName` 具有方案名稱。 若未核取 [建立方案目錄]，`SpecificSolutionName` 則為空白。|  
|`userdomain`|目前的使用者網域。|  
|`username`|目前的使用者名稱。|  
|`webnamespace`|目前的網站名稱。 這個參數用於 Web 表單範本，以保證唯一的類別名稱。 如果網站位於網頁伺服器的根目錄，此範本參數會解析為網頁伺服器的根目錄。|  
|`year`|目前的年份，格式為 YYYY。|  
  
## <a name="custom-template-parameters"></a>自訂範本參數  
 除了參數取代期間所使用的預設保留範本參數之外，您也可以指定自己的範本參數和值。如需詳細資訊，請參閱 [CustomParameters 項目 (Visual Studio 範本)](../extensibility/customparameters-element-visual-studio-templates.md)  
  
## <a name="example-replacing-files-names"></a>範例：取代檔案名稱  
 您可以搭配使用參數與 `TargetFileName` 屬性，來指定專案項目的變數檔案名稱。 例如，您可以指定 .exe 檔案使用 `$projectname$` 所指定的專案名稱作為檔案名稱。  
  
```  
<TemplateContent>  
    <ProjectItem  
        ReplaceParameters="true"  
        TargetFileName="$projectname$.exe">  
            File1.exe  
    </ProjectItem>  
      ...  
</TemplateContent>  
```  
  
## <a name="example-using-the-project-name-for-the-namespace-name"></a>範例：針對命名空間名稱使用專案名稱  
 若要在 Visual C# 類別檔案 Class1.cs 中，針對命名空間使用專案名稱，請使用下列語法：  
  
```  
#region Using directives  
  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
#endregion  
  
namespace $safeprojectname$  
{  
    public class Class1  
        {  
            public Class1()  
                {  
  
                }  
         }  
}  
```  
  
 當您參考 Class1.cs 檔時，請在專案範本的 .vstemplate 檔案中，納入下列 XML：  
  
```  
<TemplateContent>  
    <ProjectItem ReplaceParameters="true">  
        Class1.cs  
    </ProjectItem>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>另請參閱  
 [自訂範本](../ide/customizing-project-and-item-templates.md)



