# Azure Resource Manager QuickStart Templates

# Contributing guide

This is a repo that contains all the currently available Azure Resource Manager templates contributed by the community. These templates are indexed on Azure.com and available to view here http://azure.microsoft.com/en-us/documentation/templates/

To make sure your template is added to Azure.com index, please follow these guidelines. Any templates that are out of compliance will be added to the **blacklist** and not be indexed on Azure.com

1.	Every template must be contained in its own **folder**. Name this folder something that describes what your template does. Usually this naming pattern looks like **appName-osName** or **level-platformCapability** (e.g. 101-vm-user-image)
2.	The template file must be named **azuredeploy.json**
3.	The template folder must host the **scripts** that are needed for successful template execution
4.	The template folder must contain a **metadata.json** file to allow the template to be indexed on [Azure.com](http://azure.microsoft.com)
  *	Guidelines on the metadata file below
5. Include a **Readme.md** file that explains how the template works. No need to include the parameters that the template needs. We can render this on Azure.com from the template.
6. Template parameters should follow **camelCasing**
7. Try to reduce the **number of parameters** a user has to enter to deploy your template. Make things that do not need to be globally unique such as VNETs, NICs, PublicIPs, Subnets, NSGs as variables.
8. **Storage account names** need to be lower case and can't contain hyphens (-) in addition to other domain name restrictions. These also need to be globally unique.
9. Name **variables** using this scheme **templateScenarioResourceName** (e.g. simpleLinuxVMVNET, userRoutesNSG, elasticsearchPublicIP etc.) that describe the scenario rather. This ensures when a user browses all the resources in the Portal there aren't a bunch of resources with the same name (e.g. myVNET, myPublicIP, myNSG)
10. Every parameter in the template must have the **lower-case description** tag specified using the metadata property. This looks like below

  ```json
  "newStorageAccountName": {
        "type": "string",
        "metadata": {
            "description": "The name of the new storage account created to store the VMs disks"
        }
  }
  ```


See the starter template [here](https://github.com/Azure/azure-quickstart-templates/tree/master/100-starter-template-with-validation) for more information on passing validation

## Best practices

* It is a good practice to pass your template through a JSON linter to remove extraneous commas, paranthesis, brackets that may break the "Deploy to Azure" experience. Try http://jsonlint.com/ or a linter package for your favorite editing environment (Atom, Sublime Text, Visual Studio etc.)
* It's also a good idea to format your JSON for better readability. You can use a JSON formatter package for your local editor or [format online using this link](https://www.bing.com/search?q=json+formatter).

## metadata.json file

Here are the required parameters for a valid metadata.json file

To be more consistent with the Visual Studio and Gallery experience we're updating the metadata.json file structure. The new structure looks like below

    {
      "itemDisplayName": "",
      "description": "",
      "summary": "",
      "githubUsername": "",
      "dateUpdated": "<e.g. 2015-12-20>"
    }

The metadata.json file will be validated using these rules

**itemDisplayName**
*	Cannot be more than 60 characters

**description**
*	Cannot be more than 1000 characters
*	Cannot contain HTML
* This is used for the template description on the Azure.com index template details page

**summary**
*	Cannot be more than 200 characters
* This is shown for template description on the main Azure.com template index page

**githubUsername**
*	Username must be the same as the username of the author submitting the Pull Request
* This is used to display template author and Github profile pic in the Azure.com index

**dateUpdated**
*	Must be in yyyy-mm-dd format.
*	The date must not be in the future to the date of the pull request

## Starter template

A starter template is provided [here](https://github.com/Azure/azure-quickstart-templates/tree/master/100-starter-template-with-validation) for you to follow

## Template index
A searchable template index is maintained at https://azure.microsoft.com/en-us/documentation/templates/
