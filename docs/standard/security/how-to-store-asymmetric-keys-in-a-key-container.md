---
title: "Como armazenar chaves assimétricas em um contêiner de chave"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- storing asymmetric keys
- keys, asymmetric
- encryption keys
- keys, storing in key containers
- asymmetric keys [.NET Framework]
- encryption [.NET Framework], asymmetric keys
- decryption keys
ms.assetid: 0dbcbd8d-0dcf-40e9-9f0c-e3f162d35ccc
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 475139230c4b58bc6dcc307bd99eeafdc3e89e53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a>Como armazenar chaves assimétricas em um contêiner de chave
As chaves privadas assimétricas nunca devem ser armazenadas no formato textual nem como texto sem formatação no computador local. Se precisar armazenar uma chave privada, você deverá usar um contêiner de chave. Para obter mais informações sobre contêineres de chave, consulte [Noções básicas sobre nível de máquina e recipientes de chave RSA nível de usuário](http://msdn.microsoft.com/library/9a179f38-8fb7-4442-964c-fb7b9f39f5b9).  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a>Para criar uma chave assimétrica e salvá-la em um contêiner de chaves  
  
1.  Criar uma nova instância de um <xref:System.Security.Cryptography.CspParameters> classe e passe o nome que você deseja chamar o contêiner de chave para o <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> campo.  
  
2.  Criar uma nova instância de uma classe que deriva de <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe (geralmente **RSACryptoServiceProvider** ou **DSACryptoServiceProvider**) e passar criado anteriormente  **CspParameters** objeto para o construtor.  
  
### <a name="to-delete-the-key-from-a-key-container"></a>Para excluir uma chave de um contêiner de chaves  
  
1.  Criar uma nova instância de um **CspParameters** classe e passe o nome que você deseja chamar o contêiner de chave para o **CspParameters.KeyContainerName** campo.  
  
2.  Criar uma nova instância de uma classe que deriva de **AsymmetricAlgorithm** classe (geralmente **RSACryptoServiceProvider** ou **DSACryptoServiceProvider**) e passar o criado anteriormente **CspParameters** objeto para o construtor.  
  
3.  Definir o **PersistKeyInCSP** propriedade da classe que deriva de **AsymmetricAlgorithm** para **false** (**False** no Visual Basic).  
  
4.  Chamar o **limpar** método da classe que deriva de **AsymmetricAlgorithm**. Esse método libera todos os recursos da classe e limpa o contêiner de chaves.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar uma chave assimétrica, salvá-la em um contêiner de chaves, recuperar a chave posteriormente e excluir a chave do contêiner.  
  
 Observe que o código no `GenKey_SaveInContainer` método e o `GetKeyFromContainer` método é semelhante.  Quando você especifica o nome do contêiner de chaves para um objeto <xref:System.Security.Cryptography.CspParameters> e o informa a um objeto <xref:System.Security.Cryptography.AsymmetricAlgorithm> com a propriedade <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> ou <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> definida como true, acontece o seguinte:  se o contêiner de chaves com o nome especificado não existir, ele será criado e a chave persistirá.  Se o contêiner de chaves com o nome especificado existir, a chave será carregada automaticamente no objeto <xref:System.Security.Cryptography.AsymmetricAlgorithm> atual.  Assim, o método `GenKey_SaveInContainer` persiste na chave porque ele é executado primeiro. Enquanto isso, o código do método `GetKeyFromContainer` carrega a chave porque ele é executado na sequência.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
 _  
  
Public Class StoreKey  
  
    Public Shared Sub Main()  
        Try  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
        Catch e As CryptographicException  
            Console.WriteLine(e.Message)  
        End Try  
    End Sub  
  
    Public Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        ' name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key added to container:  {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub GetKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Delete the key entry in the container.  
        rsa.PersistKeyInCsp = False  
  
        ' Call Clear to release resources and delete the key from the container.  
        rsa.Clear()  
  
        Console.WriteLine("Key deleted.")  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
  
public class StoreKey  
  
{  
    public static void Main()  
    {  
        try  
        {  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
        }  
        catch(CryptographicException e)  
        {  
            Console.WriteLine(e.Message);  
        }  
  
    }  
  
    public static void GenKey_SaveInContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key added to container: \n  {0}", rsa.ToXmlString(true));  
    }  
  
    public static void GetKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : \n {0}", rsa.ToXmlString(true));  
    }  
  
    public static void DeleteKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Delete the key entry in the container.  
        rsa.PersistKeyInCsp = false;  
  
        // Call Clear to release resources and delete the key from the container.  
        rsa.Clear();  
  
        Console.WriteLine("Key deleted.");  
    }  
}  
```  
  
```Output  
Key added to container:  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key retrieved from container :  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key deleted.  
Key added to container:  
<RSAKeyValue> Key Information B</RSAKeyValue>  
Key deleted.  
```  
  
## <a name="see-also"></a>Consulte também  
 [Geração de chaves para criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [Criptografando dados](../../../docs/standard/security/encrypting-data.md)  
 [Descriptografando dados](../../../docs/standard/security/decrypting-data.md)  
 [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)