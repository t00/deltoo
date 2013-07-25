TCheckComboBox
==============

Simple themed TCheckComboBox control for Delphi - TComboBox with checkboxes

- separate Items and Values where Values can optionally be presented to a user instead of Items
- custom aggregation of values depending on user selection - checking checkboxes should trigger the event which will return a text calculated based on selections and custom algorithm, which can be say: sum all values of selected items, take maximum, average etc.
- optionally for ease of use, it should contain bitmask aggregation mode - where value can be set and retrieved by simply assigning to a string representation of integer and appropriate checked items will be translated to bit weights of items
- checks should be completely optional, when checks are disabled, the control should behave exactly like a normal TComboBox
- checks need to use windows themes and look alike all other checkboxes
- it should be as simple as possible but not any simpler - no copy + paste from Controls.pas or StdCtrls.pas

The control may have some bugs as it was not heavily tested and for best experience depends on some settings in DFM:

    AutoComplete = False
    Style = csDropDownList

Having said that, for all those who seek a free TCheckComboBox which have all or some of aforementioned features, feel free to use it.

TGenericStringList<T>
==============

	A generic list with benefits of both TStringList (persistent, sortable, can be published) and TList<> (generic list containing TObject descendants).
	This stores both string and object so is similar to the Tuple<string, T> in C#.
	
	sl := TGenericStringList<TSomething>.Create;
	sl.AddObject('Here=There', TSomething.Create(123));
	if sl.Values['Here'] = 'There' then
        sl[0].Value := sl[0].Value + 1; // 124
	
TPersistentStringList<T>
==============

TGenericStringList with deep cloning ability, each object contained in the collection will be recreated wher assigning - parameterless constructor is required.

	redApple := TApple.Create('Red');
    applesOnTheTree := TPersistentStringList<TApple>.Create;
	applesOnTheTree.AddObject('branch1', redApple);
	applesOnTheGround := TPersistentStringList<TApple>.Create;
	applesOnTheGround.Assign(applesOnTheTree);
	applesOnTheGround[0].Color := 'Yellow'; // change cloned TApple's color
	redColor := applesOnTheTree[0].Color; // still 'Red'

==============

----------------

Copyright (C) 2008-2013 Michal Turecki

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL
THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
DEALINGS IN THE SOFTWARE.

History:
  v1.0 2012-12-12 First public release (http://turecki.net/node/14)
