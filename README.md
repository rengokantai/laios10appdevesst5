# laios10appdevesst5
##1

##2 Create a basic table view data source
Make the connection and then you can see in the connections inspector the data source is set to
be the view controller and that tells the table view it's getting it's data from the view controller class.  

####01:24
ViewController.swift
```
class ViewController:UIViewController,UITableViewDataSource{
  //two methods, in swift3
  func tableView(_ tableView:UITableView,numberOFRowsInSection section:Int)->Int{return 4}
  
  func tableView(_ tableView:UITableView,cellForRowAt indexPath:IndexPath)->UITableViewCell{
     let cell = UITableViewCell()
     cell.textLabel?.text=""
     return cell
   }
}
```
###3 Load an array into a table view
ViewController.swift
```
let data:[String]=["a","b"]
func tableView(_ tableView:UITableView,numberOFRowsInSection section:Int)->Int{return data.count}

  func tableView(_ tableView:UITableView,cellForRowAt indexPath:IndexPath)->UITableViewCell{
     let cell = UITableViewCell()
     cell.textLabel?.text=data[indexPath.row]
     return cell
   }
```
###4 Reuse table view cells
iOS actually has a built in feature to recycle table view cells, and that way of recycling is accessible through the table view object, so we can call tableView, which is going to be a parameter that comes in when this method is called, so that's right here, our table view.  

####00:56
ViewController.swift
```
  func tableView(_ tableView:UITableView,cellForRowAt indexPath:IndexPath)->UITableViewCell{
     let cell = tableView.dequeueReusableCell(withIdentifier:"cell",for:IndexPath)
     cell.textLabel?.text=data[indexPath.row]
     return cell
   }
```
in storyboard, (Table View)  
Content->Dynamic Prototype, Prorotype Cells->1  

in storyboard, (Table View Cell)  
Style=>Custom, Identifier->cell  (in code:withIdentifier:"cell")  

###5 Group sections in table views
multid array
```
let data:[[String]]=[["a","b"],["c","d"]]
func tableView(_ tableView:UITableView,numberOFRowsInSection section:Int)->Int{return data[section].count}
func numberOfSections(in tableView:UITableView)->Int{ return data.count}
func tableView(_ tableView:UITableView,cellForRowAt indexPath:IndexPath)->UITableViewCell{
   let cell = tableView.dequeueReusableCell(withIdentifier:"cell",for:IndexPath)
   cell.textLabel?.text=data[indexPath.section][indexPath.row]
   return cell
}
```
####03:38
Table View->  
Style: Plain->Grouped
