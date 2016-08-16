//
//  ColorPlus.swift
//  Strooper
//
//  Created by Horacio Garza on 24/07/16.
//  Copyright © 2016 HGarz Studios. All rights reserved.
//

import Foundation
import UIKit

struct ColorPlus{
  
  private var defaultColors = [String:String]()
  private var defaultColorsKeys:[String]?
  
  /**
   Constructor
   */
  init(){
    
    defaultColors["Red"] = "#F44336"
    defaultColors["Pink"] = "#EC407A"
    defaultColors["Purple"] = "#9C27B0"
    defaultColors["Blue"] = "#3F51B5"
    defaultColors["Green"] = "#4CAF50"
    defaultColors["Yellow"] = "#FFEB3B"
    defaultColors["Orange"] = "#FF9800"
    defaultColors["Brown"] = "#795548"
    
    defaultColorsKeys = Array(defaultColors.keys)
    
  }
  
  /**
   getRandomColor is a function of the ColorPlus class.
   
   - returns: A dictionary containing the name of the color and the hex value
   */
  func getRandomColor() -> (String, String){
    
    var randomIndex:Int?
    randomIndex = Int(arc4random_uniform(UInt32(defaultColorsKeys!.count)))
    
    
    
    let name:String = defaultColorsKeys![randomIndex!]
    let colorHexValue:String = defaultColors[name]!
    let color = (name, colorHexValue)
    
    return color
  }
  
  
  /**
   Adds a color to the dictionary of colors.
   
   - parameter name:    Name of the color
   - parameter hexCode: Hexadecimal code for the color
   */
  mutating func addColor(name:String, hexCode:String) {
    
    defaultColors[name] = hexCode
    
  }
  
  /**
   Returns an array of the DefaultColors variable.
   
   - returns: Dictionary with the color's name and it's UIColor variable.
   */
  mutating func getRandomColorArray() -> NSDictionary{
    
    var randomColors = Dictionary<String, UIColor>()
    defaultColorsKeys?.shuffle((defaultColorsKeys?.count)!)
    
    
    
    for i in 0..<(defaultColorsKeys?.count)! {
      
      let key = defaultColorsKeys![i]
      let color = getColorByHex(defaultColors[key]!)
      
      
      randomColors[key] = color
    
    }
    
    
    return randomColors
  }
  
  /**
   Returns a custom size array of the DefaultColors variable.
   
   - returns: Dictionary with the color's name and it's UIColor variable.
   */
  mutating func getRandomColorArray(size: Int) -> NSDictionary{
    
    var randomColors = Dictionary<String, UIColor>()
    defaultColorsKeys?.shuffle((defaultColorsKeys?.count)!)
    
    for i in 0..<size {
      
      let key = defaultColorsKeys![i]
      let color = getColorByHex(defaultColors[key]!)
      
      randomColors[key] = color
      
    }
    
    return randomColors
  }
  
  
  /**
   Gets a UIColor variable from his Hexadecimal code.
   
   - parameter hexCode: Hexadecimal code, example "#FFFFFF"
   
   - returns: UIColor variable
   */
  func getColorByHex(hexCode: String) -> UIColor {
    
    var hexCodeMod = hexCode
    if (hexCodeMod.hasPrefix("#")) {
      
      let index = hexCodeMod.startIndex.advancedBy(0)
      hexCodeMod.removeAtIndex(index)
      
    }
    
    let rString: String = (hexCodeMod as NSString).substringToIndex(2)
    let gString = ((hexCodeMod as NSString).substringFromIndex(2) as NSString).substringToIndex(2)
    let bString = ((hexCodeMod as NSString).substringFromIndex(4) as NSString).substringToIndex(2)
    
    
    /// https://gist.github.com/arshad/de147c42d7b3063ef7bc
    var r: CUnsignedInt = 0, g: CUnsignedInt = 0, b: CUnsignedInt = 0;
    NSScanner(string: rString).scanHexInt(&r)
    NSScanner(string: gString).scanHexInt(&g)
    NSScanner(string: bString).scanHexInt(&b)
    
    
    
    let color:UIColor = UIColor(red: CGFloat(r) / CGFloat(255.0), green: CGFloat(g) / CGFloat(255.0), blue: CGFloat(b) / CGFloat(255.0), alpha: CGFloat(1))
    return color
    
  }
  
  
  
  
  
}


