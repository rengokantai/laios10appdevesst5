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
  
  func tableView(_ tableView:UITableView,cellForRowAt indexPath:IndexPath)->UITableCell{
     let cell = UITableViewCell()
     cell.textLabel?.text=""
     return cell
   }
}
```
