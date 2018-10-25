---
title: 示範範例 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 23
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5bcdb1e026808071167b23b829597a4d28775c02
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880652"
---
# <a name="demo-sample"></a>示範範例
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

以下程序會示範如何建立的範例[逐步解說： 分析 C/c + + 程式碼的缺失](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md)。 建立程序：  
  
- A[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]命名 CppDemo 解決方案。  
  
- 靜態程式庫專案命名為 CodeDefects。  
  
- 靜態程式庫專案命名為註解。  
  
  程序也會提供靜態程式庫標頭和.cpp 檔的程式碼。  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>建立 CppDemo 解決方案和 CodeDefects 專案  
  
1.  按一下 **檔案**功能表上，指向**新增**，然後按一下**新專案**。  
  
2.  在 **專案類型**樹狀目錄清單中，如果 Visual c + + 不是您的預設語言，在 VS 中展開**其他語言**。  
  
3.  依序展開**Visual c + +**，然後按一下**一般**。  
  
4.  在 **範本**，按一下**空白專案**。  
  
5.  在 **名稱**文字方塊中，輸入**CodeDefects**。  
  
6.  選取 **為方案建立目錄**核取方塊。  
  
7.  在 **方案名稱**文字方塊中，輸入**CppDemo**。  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>將 CodeDefects 專案設定為靜態程式庫  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**CodeDefects** ，然後按一下**屬性**。  
  
2.  依序展開**組態屬性**，然後按一下**一般**。  
  
3.  在 **一般**清單中，選取的文字資料行中，旁邊**目標副檔名**，然後輸入 **.lib**。  
  
4.  在**專案預設值**，按一下資料行旁邊**組態類型**，然後按一下**靜態程式庫 (.lib)**。  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>加入 CodeDefects 專案中的標頭和來源檔案  
  
1.  在 方案總管 中，展開**CodeDefects**，以滑鼠右鍵按一下**標頭檔**，按一下 **新增**，然後按一下**新項目**。  
  
2.  在 [**加入新項目**] 對話方塊中，按一下**程式碼**，然後按一下**標頭檔 (.h)**。  
  
3.  在 **名稱**方塊中，輸入**Bug.cpp** ，然後按一下 **新增**。  
  
4.  複製下列程式碼，並將它貼至**Bug.cpp**檔案中[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]編輯器。  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  在 [方案總管] 中，以滑鼠右鍵按一下**原始程式檔**，指向**新增**，然後按一下**新項目**。  
  
6.  在 **加入新項目** 對話方塊中，按一下  **c + + 檔 (.cpp)**  
  
7.  在 **名稱**方塊中，輸入**Bug.cpp** ，然後按一下 **新增**。  
  
8.  下列程式碼複製並貼到 Bug.h 檔案[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]編輯器。  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. 按一下 **檔案**功能表，然後再按一下**全部儲存**。  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>新增註解的專案，並將它設定為靜態程式庫  
  
1.  在 [方案總管] 中，按一下**CppDemo**，指向**新增**，然後按一下**新專案**。  
  
2.  在**加入新的專案**對話方塊方塊中，展開 Visual c + + 中，按一下**一般**，然後按一下**空專案**。  
  
3.  在 **名稱**文字方塊中，輸入**註釋**，然後按一下**新增**。  
  
4.  在 [方案總管] 中，以滑鼠右鍵按一下**註釋**，然後按一下**屬性**。  
  
5.  依序展開**組態屬性**，然後按一下**一般**。  
  
6.  在 **一般**清單中，選取的文字資料行中，旁邊**目標副檔名**，然後輸入 **.lib**。  
  
7.  在**專案預設值**，按一下資料行旁邊**組態類型**，然後按一下**靜態程式庫 (.lib)**。  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>加入註解專案中的標頭檔和原始程式檔  
  
1.  在 [方案總管] 中，展開**註釋**，以滑鼠右鍵按一下**標頭檔**，按一下**新增**，然後按一下**新項目**。  
  
2.  在 [**加入新項目**] 對話方塊中，按一下**標頭檔 (.h)**。  
  
3.  在 **名稱**方塊中，輸入**annotations.h** ，然後按一下 **新增**。  
  
4.  複製下列程式碼，並將它貼至**annotations.h**檔案中[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]編輯器。  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  在 [方案總管] 中，以滑鼠右鍵按一下**原始程式檔**，指向**新增**，然後按一下**新項目**。  
  
6.  在 **加入新項目** 對話方塊中，按一下**程式碼**，然後按一下  **c + + 檔 (.cpp)**  
  
7.  在 **名稱**方塊中，輸入**annotations.cpp** ，然後按一下 **新增**。  
  
8.  複製下列程式碼，並將它貼至**annotations.cpp**檔案中[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]編輯器。  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. 按一下 **檔案**功能表，然後再按一下**全部儲存**。



