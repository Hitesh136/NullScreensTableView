# NullScreensTableView
Add Null Screen in tableview's background 

```swift
 extension UITableView{
 func setNoDataView(image: UIImage? = nil, message: String? = nil ) {
        self.removeNoDataView()
        self.separatorStyle  = .none
        
        let noDataLabel: UILabel = UILabel()
        if let msg = message {
            noDataLabel.text = msg
        }
        else {
            noDataLabel.text = "No Data Available"
        }
        
        noDataLabel.textColor     = UIColor.black
        noDataLabel.textAlignment = .center
        
        let detailImgV = UIImageView()
        if let img = image {
            detailImgV.image = img
        }
        else {
            detailImgV.image = UIImage(named: "ic-data")
        }
        
        detailImgV.contentMode = .scaleAspectFit
        detailImgV.widthAnchor.constraint(equalToConstant: 120).isActive = true
        detailImgV.heightAnchor.constraint(equalToConstant: 120).isActive = true
        
        let verticalSV = UIStackView()
        verticalSV.axis = .vertical
        verticalSV.spacing = 0
        verticalSV.alignment = .center
        verticalSV.distribution = .fill
        verticalSV.translatesAutoresizingMaskIntoConstraints = false
        verticalSV.addArrangedSubview(detailImgV)
        verticalSV.addArrangedSubview(noDataLabel)
        
        self.addSubview(verticalSV)
        verticalSV.centerXAnchor.constraint(equalTo: self.centerXAnchor).isActive = true
        verticalSV.centerYAnchor.constraint(equalTo: self.centerYAnchor).isActive = true
        verticalSV.widthAnchor.constraint(equalToConstant: ScreenSize.width).isActive = true
        verticalSV.heightAnchor.constraint(equalToConstant: 160).isActive = true
    }
    
    func removeNoDataView(_ seperator: UITableViewCellSeparatorStyle = .singleLine) {
        for view in self.subviews {
            if view is UIStackView {
                view.removeFromSuperview()
            }
        }
    }
    }
```        
