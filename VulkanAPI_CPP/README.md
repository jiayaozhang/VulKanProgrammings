## Errors fixed after debugging

* In `VulkanValidation.h` file we need to change the validation layers

from 

`VK_LAYER_LUNARG_standard_validation`

to 

`VK_LAYER_KHRONOS_validation`

* when i install the assimp, I found that I should totally not use the x86 assimp, if so all the codes would not compile.

Therefore we need to install 

`    * git clone https://github.com/Microsoft/vcpkg.git`
`    * cd vcpkg`
`    * ./bootstrap-vcpkg.sh`
`    * ./vcpkg integrate install`
`    * vcpkg install assimp:x64-windows`

We need to make our default as x64 , so we need to set the `environment path` in our system.

* Laater we have to add our model in main.cpp as `Models/chopper.obj` and put the bmp files in the `Textures` folder.

* If we encounter some errors like `& have to be the L-value`
  Then we need to modify the codes below. 


We need to change the Mesh.cpp here.

`Model& Mesh::getModel()
{
	return model;
}`

And we need to change the Mesh.h here.

`	Model& getModel();`

Also learn more stuff about Cmakelist.txt 

How to fixed the 

`find package()` 

* All the vulkan and glfw or glad api need to be target at x64 not x84 

* Otherwise it would show different error! Keep focus !

* For the last 17 and 18 chapters

We need to focus here

`				&thisModel.getMesh(0)->getModel());		` 

`Add a getMesh(0) here`

* If encounter some errors like below
`$ git push`
`To github.com:jiayaozhang/VulKanProgrammings.git`
` ! [rejected]        main -> main (fetch first)`
`error: failed to push some refs to 'github.com:jiayaozhang/VulKanProgrammings.git`
`hint: Updates were rejected because the remote contains work that you do`

This is the connnection errors, we just have to do 

`git config --global http.sslVerify "false"`

## find_package

语法 : `find_package(<PackageName> [version] [EXACT] [QUIET] [MODULE] [REQUIRED] [[COMPONENTS] [components...]] [OPTIONAL_COMPONENTS components...] [NO_POLICY_SCOPE])`

查找并从外部项目加载设置。 <PackageName>_FOUND 将设置为指示是否找到该软件包。 找到软件包后，将通过软件包本身记录的变量和“导入的目标”提供特定于软件包的信息。 该QUIET选项禁用信息性消息，包括那些如果未找到则表示无法找到软件包的消息REQUIRED。REQUIRED如果找不到软件包，该选项将停止处理并显示一条错误消息。

COMPONENTS选件后（或REQUIRED选件后，如果有的话）可能会列出所需组件的特定于包装的列表 。后面可能会列出其他可选组件OPTIONAL_COMPONENTS。可用组件及其对是否认为找到包的影响由目标包定义。