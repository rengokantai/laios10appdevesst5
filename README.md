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
Style->Custom, Identifier->cell  (in code:withIdentifier:"cell")  

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


###6 Add section headers to table views
```
let data:[[String]]=[["a","b"],["c","d"]]
let headers:[String]=["section1","section2"]

func tableView(_ tableView:UITableView, titleForHeaderInSection section:Int)->String?{
  return headers[section]
}
```
###7 Add subtitles and images to cells
####00:31
Table View Cell->Style:Subtitle

####01:20
```
let data:[[String]]=[["a","b"],["c","d"]]
let subs:[[String]]=[["suba","subb"],["subc","subd"]]
let headers:[String]=["section1","section2"]
func tableView(_ tableView:UITableView,cellForRowAt indexPath:IndexPath)->UITableViewCell{
   let cell = tableView.dequeueReusableCell(withIdentifier:"cell",for:IndexPath)
   cell.textLabel?.text=data[indexPath.section][indexPath.row]
   cell.detailTextLabel?.text=subs[indexPath.section][indexPath.row]
   return cell
}
```
####02:36 add pics
star.png, star@2x.png, star@3x.png  


####03:27
Table View Cell->Image,set star(all cells same image)  

####04:12
set in code:
```
cell.imageView?.image = UIImage(named:"star")
```

###8 Create a custom table view cell
creat new file CustomCell, subclass of UITableViewCell

####01:41
storyboard->Identity inspecor->custom class:CustomCell   

####03:14
create a  label, drag the label to CustomCell  opt+click open assitant editor  

####04:16
```
func tableView(_ tableView:UITableView,cellForRowAt indexPath:IndexPath)->UITableViewCell{
   let cell = tableView.dequeueReusableCell(withIdentifier:"cell",for:IndexPath) as! CustomCell
   cell.label.text=data[indexPath.section][indexPath.row]
   return cell
}
```





