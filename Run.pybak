from javax.swing import *
from java.awt import *
from java.awt.event import *
from java.lang import *
from random import *

app = JFrame("Hi! I'm a Image Proccessing Software", size = (700, 135))
app.setLocationRelativeTo(None)
app.setLayout(None)

path = pickAFile();
pic = makePicture(path)
show(pic)
em_pic = makeEmptyPicture(getHeight(pic), getWidth(pic))
for i in getPixels(em_pic):
    setColor(i,white)
default = [];
for i in getPixels(pic):
    color = getColor(i)
    default.append(color)

iconSunset = ImageIcon("D:Final Project\\icon\\sun.png")
icondecreasedRed = ImageIcon("D:Final Project\\icon\\decreasedRed.png")
icondecreasedBlue = ImageIcon("D:Final Project\\icon\\decreasedBlue.png")
icondecreasedGreen = ImageIcon("D:Final Project\\icon\\decreasedGreen.png")
iconRoot = ImageIcon("D:\\Final Project\\icon\\root.png")
iconLighten = ImageIcon("D:\\Final Project\\icon\\lighten.png")
iconDarken = ImageIcon("D:\\Final Project\\icon\\darken.png")
iconNegative = ImageIcon("D:\\Final Project\\icon\\negative.png")
iconGreyscale = ImageIcon("D:\\Final Project\\icon\\greyscale.png")
iconMirrorLeft = ImageIcon("D:\\Final Project\\icon\\mirrorLeft.png")
iconMirrorTop = ImageIcon("D:\\Final Project\\icon\\mirrorTop.png")
iconMirrorRight = ImageIcon("D:\\Final Project\\icon\\mirrorRight.png")
iconMirrorBottom = ImageIcon("D:\\Final Project\\icon\\mirrorBottom.png")
iconRotate = ImageIcon("D:\\Final Project\\icon\\rotate.png")
iconText = ImageIcon("D:\\Final Project\\icon\\text.png")
iconLine = ImageIcon("D:\\Final Project\\icon\\line.png")
iconRectangle = ImageIcon("D:\\Final Project\\icon\\rectangle.png")
iconCrop = ImageIcon("D:\\Final Project\\icon\\crop.png")

# ------------------------------ EVENT ----------------------------
def btn_open_Click(event):
    path = pickAFile();
    pic = makePicture(path)
    show(pic)
    
def btn_save_Click(event):
    writePictureTo(pic, "D:\\Final Project\\save\\%d%d%d%d.jpg" % (randint(0, 9), randint(0, 9), randint(0, 9), randint(0, 9)))
     
def btn_root_Click(event):
    pos = 0
    for i in getPixels(pic):
        setColor(i, default[pos])
        pos = pos + 1
    repaint(pic)
    
def btn_plus_Click(event):
    if float(txt_level.text) < 2.0:
        txt_level.text = str(round(float(txt_level.text) + 0.1, 2))
    
def btn_subtract_Click(event):
    if float(txt_level.text) > 0.1:
        txt_level.text = str(round(float(txt_level.text) - 0.1, 2))

def mnu_decreasedRed_Click(event):
    for i in getPixels(pic):
        setRed(i, getRed(i) * float(txt_level.text))
    repaint(pic)
     
def mnu_decreasedGreen_Click(event):
    for i in getPixels(pic):
        setGreen(i, getGreen(i) * float(txt_level.text))
    repaint(pic)

def mnu_decreasedBlue_Click(event):
    for i in getPixels(pic):
        setBlue(i, getBlue(i) * float(txt_level.text))
    repaint(pic)

def mnu_sunset_Click(event):
     for i in getPixels(pic):
        pxgreen = getGreen(i)
        setGreen(i, pxgreen * float(txt_level.text))
     for i in getPixels(pic):
        pxblue = getBlue(i)
        setBlue(i, pxblue * float(txt_level.text))
     repaint(pic)

def mnu_lighten_Click(event):
    for i in getPixels(pic):
        value = getColor(i)
        value = makeLighter(value)
        setColor(i, value)
    repaint(pic)
 
def mnu_darken_Click(event):
    for i in getPixels(pic):
        value = getColor(i)
        value = makeDarker(value)
        setColor(i, value)
    repaint(pic) 
    
def mnu_negative_Click(event):
    for i in getPixels(pic):
        red = getRed(i)
        green = getGreen(i)
        blue = getBlue(i)
        negColor = makeColor(255 - red, 255 - green, 255 - blue / 5)
        setColor(i, negColor)                 
    repaint(pic)
    
def mnu_greyscale_Click(event):
    for i in getPixels(pic):
        grey = (getRed(i) + getGreen(i) + getBlue(i))/3
        setColor(i, makeColor(grey, grey, grey))
    repaint(pic) 
    
def mnu_mirrorLeft_Click(event):
    point = getWidth(pic)/2
    for he in range(0, getHeight(pic)):
        for wi in range(0, point):
            pxLeft = getPixel(pic, wi, he)
            pxRight = getPixel(pic, getWidth(pic) - wi - 1, he)
            coLeft = getColor(pxLeft)
            setColor(pxRight, coLeft)
    repaint(pic)
    
def mnu_mirrorTop_Click(event):
    point = getHeight(pic)/2
    for he in range(0, point):
        for wi in range(0, getWidth(pic)):
            pxTop = getPixel(pic, wi, he)
            pxBottom = getPixel(pic, wi, getHeight(pic) - he - 1)
            coTop = getColor(pxTop)
            setColor(pxBottom, coTop)
    repaint(pic)
    
def mnu_mirrorRight_Click(event):
    point = getWidth(pic)/2
    for he in range(0, getHeight(pic)):
        for wi in range(point, getWidth(pic)):
            pxRight = getPixel(pic, wi, he)
            pxLeft = getPixel(pic, getWidth(pic) - wi - 1, he)
            coRight = getColor(pxRight)
            setColor(pxLeft, coRight)
    repaint(pic)
    
def mnu_mirrorBottom_Click(event):
    mirrorPoint = getHeight(pic)/2
    height = getHeight(pic)
    for he in range(0, mirrorPoint):
        for wi in range(0, getWidth(pic)):
            pxabove = getPixel(pic, wi, he)
            pxunder = getPixel(pic, wi, height - he - 1)
            colorAbove = getColor(pxunder)
            setColor(pxabove, colorAbove)
    repaint(pic)
    
def mnu_rotate_Click(event):
    targetX = 0
    for x in range(0, getWidth(pic)):
        targetY = 0
        for y in range(0, getHeight(pic)):
            get_oldColor = getColor(getPixel(pic, x, y))
            setColor(getPixel(em_pic, targetY, targetX), get_oldColor)
            targetY = targetY + 1
        targetX = targetX + 1
    repaint(em_pic)
    show(em_pic)
    writePictureTo(em_pic, "D:\\Final Project\\save\\rotate.jpg")
    
def mnu_crop_Click(event):
    cropForm = JFrame("Input Value", size = (400, 170))
    cropForm.setLocationRelativeTo(None)
    cropForm.setLayout(None)
    
    def btn_apply_Click(event):
        crop_pic = makeEmptyPicture(int(txt_width.text), int(txt_height.text))
        for i in getPixels(crop_pic):
            setColor(i,white)
        posX = int(txt_posX.text)
        poxY = int(txt_posY.text)
        width = int(txt_width.text)
        height = int(txt_height.text)
        targetX = 0
        for he in range(posY, posY + height):
            targetY = 0
            for wi in range(posX, posX + width):
                color = getColor(getPixel(pic, wi, he))
                setColor(getPixel(crop_pic, targetX, targetY), color)
                targetY = targetY + 1
            targetX = targetX + 1
        repaint(crop_pic)
        show(crop_pic)
    
    lbl_PosX = JLabel("Position X")
    lbl_PosX.setBounds(5, 5, 100, 25)
    lbl_PosY = JLabel("Position Y")
    lbl_PosY.setBounds(215, 5, 100, 25)
    txt_PosX = JTextField()
    txt_PosX.setBounds(110, 5, 50, 25)
    txt_PosY = JTextField()
    txt_PosY.setBounds(310, 5, 50, 25)
    lbl_width = JLabel("Width")
    lbl_width.setBounds(5, 40, 100, 25)
    lbl_height = JLabel("Height")
    lbl_height.setBounds(215, 40, 100, 25)
    txt_width = JTextField()
    txt_width.setBounds(110, 40, 50, 25)
    txt_height = JTextField()
    txt_height.setBounds(310, 40, 50, 25)
    btn_apply = JButton("Apply", actionPerformed = btn_apply_Click, background = white)
    btn_apply.setBounds(150, 80, 100, 25)
    
    cropForm.add(lbl_PosX)
    cropForm.add(lbl_PosY)
    cropForm.add(txt_PosX)
    cropForm.add(txt_PosY)
    cropForm.add(lbl_width)
    cropForm.add(lbl_height)
    cropForm.add(txt_width)
    cropForm.add(txt_height)
    cropForm.add(btn_apply)
    cropForm.visible = True
    
def mnu_text_Click(event):
    textForm = JFrame("Input value", size = (300, 150))
    textForm.setLocationRelativeTo(None)
    textForm.setLayout(None)
    
    def btn_ok_Click(event):
        addText(pic, int(txt_posX.text), int(txt_posY.text), txt_string.text)
        repaint(pic)
    
    lbl_posX = JLabel("Position X")
    lbl_posX.setBounds(5, 5, 60, 25)
    lbl_posY = JLabel("Position Y")
    lbl_posY.setBounds(135, 5, 60, 25)
    lbl_string = JLabel("Content")
    lbl_string.setBounds(5, 40, 60, 25)
    txt_posX = JTextField()
    txt_posX.setBounds(70, 5, 50, 25)
    txt_posY = JTextField()
    txt_posY.setBounds(200, 5, 50, 25)
    txt_string = JTextField()
    txt_string.setBounds(70, 40, 180, 25)
    btn_ok = JButton("Apply", actionPerformed = btn_ok_Click, background = white)
    btn_ok.setBounds(120, 70, 70, 25)
    
    textForm.add(lbl_posX)
    textForm.add(lbl_posY)
    textForm.add(lbl_string)
    textForm.add(txt_posX)
    textForm.add(txt_posY)
    textForm.add(txt_string)
    textForm.add(btn_ok)
    textForm.visible = True
   
def mnu_line_Click(event):
    textLine = JFrame("Input value", size = (400, 170))
    textLine.setLocationRelativeTo(None)
    textLine.setLayout(None)
    
    def btn_apply_Click(event):
        addLine(pic, int(txt_startPosX.text), int(txt_startPosY.text), int(txt_endPosX.text), int(txt_endPosY.text))
        repaint(pic)
    
    lbl_startPosX = JLabel("Position start X")
    lbl_startPosX.setBounds(5, 5, 100, 25)
    lbl_startPosY = JLabel("Position start Y")
    lbl_startPosY.setBounds(215, 5, 100, 25)
    txt_startPosX = JTextField()
    txt_startPosX.setBounds(110, 5, 50, 25)
    txt_startPosY = JTextField()
    txt_startPosY.setBounds(310, 5, 50, 25)
    lbl_endPosX = JLabel("Position end X")
    lbl_endPosX.setBounds(5, 50, 100, 25)
    lbl_endPosY = JLabel("Position end Y")
    lbl_endPosY.setBounds(215, 50, 100, 25)
    txt_endPosX = JTextField()
    txt_endPosX.setBounds(110, 50, 50, 25)
    txt_endPosY = JTextField()
    txt_endPosY.setBounds(310, 50, 50, 25)
    btn_apply = JButton("Apply", actionPerformed = btn_apply_Click, background = white)
    btn_apply.setBounds(150, 95, 100, 25)
    
    textLine.add(lbl_startPosX)
    textLine.add(lbl_startPosY)
    textLine.add(txt_startPosX)
    textLine.add(txt_startPosY)
    textLine.add(lbl_endPosX)
    textLine.add(lbl_endPosY)
    textLine.add(txt_endPosX)
    textLine.add(txt_endPosY)
    textLine.add(btn_apply)
    textLine.visible = True 

def mnu_rectangle_Click(event):
    recForm = JFrame("Input value", size = (400, 220))
    recForm.setLocationRelativeTo(None)
    recForm.setLayout(None)
    data = ("white", "red", "yellow", "green", "blue", "black", "orange")
    
    def btn_apply_Click(event):
        if chb_fill.isSelected():
            addRectFilled(pic, int(txt_PosX.text), int(txt_PosY.text), int(txt_width.text), int(txt_height.text), white)
        else:
            addRect(pic, int(txt_PosX.text), int(txt_PosY.text), int(txt_width.text), int(txt_height.text))
        repaint(pic)
    
    lbl_PosX = JLabel("Position X")
    lbl_PosX.setBounds(5, 5, 100, 25)
    lbl_PosY = JLabel("Position Y")
    lbl_PosY.setBounds(215, 5, 100, 25)
    lbl_color = JLabel("Color")
    lbl_color.setBounds(5, 80, 100, 25)
    txt_PosX = JTextField()
    txt_PosX.setBounds(110, 5, 50, 25)
    txt_PosY = JTextField()
    txt_PosY.setBounds(310, 5, 50, 25)
    lbl_width = JLabel("Width")
    lbl_width.setBounds(5, 40, 100, 25)
    lbl_height = JLabel("Height")
    lbl_height.setBounds(215, 40, 100, 25)
    txt_width = JTextField()
    txt_width.setBounds(110, 40, 50, 25)
    txt_height = JTextField()
    txt_height.setBounds(310, 40, 50, 25)
    cbo_color = JComboBox(data)
    cbo_color.setBounds(110, 80, 70, 25)
    chb_fill = JRadioButton("Fill Color")
    chb_fill.setBounds(80, 110, 80, 25)
    chb_nofill = JRadioButton("No Fill")
    chb_nofill.setBounds(230, 110, 80, 25)
    btg_group = ButtonGroup()
    btg_group.add(chb_fill)
    btg_group.add(chb_nofill)
    btn_apply = JButton("Apply", actionPerformed = btn_apply_Click, background = white)
    btn_apply.setBounds(150, 145, 100, 25)
    
    recForm.add(lbl_PosX)
    recForm.add(lbl_PosY)
    recForm.add(lbl_color)
    recForm.add(txt_PosX)
    recForm.add(txt_PosY)
    recForm.add(lbl_width)
    recForm.add(lbl_height)
    recForm.add(txt_width)
    recForm.add(txt_height)
    recForm.add(cbo_color)
    recForm.add(btn_apply)
    recForm.add(chb_fill)
    recForm.add(chb_nofill)
    recForm.visible = True  

btn_open = JButton("Open", actionPerformed = btn_open_Click, background = Color(218, 220, 220))
btn_open.setBounds(5, 3, 80, 28)

btn_save = JButton("Save", actionPerformed = btn_save_Click, background =  Color(218, 220, 220))
btn_save.setBounds(90, 3, 80, 28)

btn_root = JButton("", iconRoot, actionPerformed = btn_root_Click, background = white)
btn_root.setBounds(3, 3, 50, 50)

lbl_level = JLabel("Level of Effectivity", SwingConstants.RIGHT)
lbl_level.setBounds(392, 5, 120, 20)

btn_plus = JButton("+", actionPerformed = btn_plus_Click, background = white)
btn_plus.setBounds(520, 1, 45, 30)

txt_level = JTextField("1.0")
txt_level.setBounds(570, 3, 38, 25)

btn_subtract = JButton("-", actionPerformed = btn_subtract_Click, background = white)
btn_subtract.setBounds(615, 1, 45, 30)

# ------------------------------ MENU --------------------------
mnu_bar = JMenuBar()
mnu_bar.setBounds(190, 3, 492, 28)

mnu_effect = JMenu("Effect")
mnu_action = JMenu("Action")
mnu_draw = JMenu("Draw")

mnu_decreasedRed = JMenuItem("Decrease Red", icondecreasedRed, actionPerformed = mnu_decreasedRed_Click)
mnu_decreasedGreen = JMenuItem("Decrease Green", icondecreasedGreen, actionPerformed = mnu_decreasedGreen_Click)
mnu_decreasedBlue = JMenuItem("Decrease Blue", icondecreasedBlue, actionPerformed = mnu_decreasedBlue_Click)
mnu_sunset = JMenuItem("SunSet",iconSunset, actionPerformed = mnu_sunset_Click)
mnu_lighten = JMenuItem("Lighten",iconLighten, actionPerformed = mnu_lighten_Click)
mnu_darken = JMenuItem("Darken",iconDarken, actionPerformed = mnu_darken_Click)
mnu_negative = JMenuItem("Negative",iconNegative, actionPerformed = mnu_negative_Click)
mnu_greyscale = JMenuItem("Grey Scale",iconGreyscale, actionPerformed = mnu_greyscale_Click)
mnu_mirrorLeft = JMenuItem("Mirror Left",iconMirrorLeft, actionPerformed = mnu_mirrorLeft_Click)
mnu_mirrorTop = JMenuItem("Mirror Top",iconMirrorTop, actionPerformed = mnu_mirrorTop_Click)
mnu_mirrorRight = JMenuItem("Mirror Right",iconMirrorRight, actionPerformed = mnu_mirrorRight_Click)
mnu_mirrorBottom = JMenuItem("Mirror Bottom",iconMirrorBottom, actionPerformed = mnu_mirrorBottom_Click)
mnu_rotate = JMenuItem("Rotate",iconRotate, actionPerformed = mnu_rotate_Click)
mnu_crop = JMenuItem("Crop",iconCrop, actionPerformed = mnu_crop_Click)
mnu_text = JMenuItem("Text",iconText, actionPerformed = mnu_text_Click)
mnu_line = JMenuItem("Line",iconLine, actionPerformed = mnu_line_Click)
mnu_rectangle = JMenuItem("Rectangle",iconRectangle, actionPerformed = mnu_rectangle_Click)

mnu_effect.add(mnu_decreasedRed)
mnu_effect.add(mnu_decreasedGreen)
mnu_effect.add(mnu_decreasedBlue)
mnu_effect.add(mnu_sunset)
mnu_effect.add(mnu_lighten)
mnu_effect.add(mnu_darken)
mnu_effect.add(mnu_negative)
mnu_effect.add(mnu_greyscale)
mnu_action.add(mnu_mirrorLeft)
mnu_action.add(mnu_mirrorRight)
mnu_action.add(mnu_mirrorTop)
mnu_action.add(mnu_mirrorBottom)
mnu_action.add(mnu_rotate)
mnu_action.add(mnu_crop)
mnu_draw.add(mnu_text)
mnu_draw.add(mnu_line)
mnu_draw.add(mnu_rectangle)

mnu_bar.add(mnu_effect)
mnu_bar.add(mnu_action)
mnu_bar.add(mnu_draw)

# ------------------------------ PANEL ----------------------------
effectPanel = JPanel()
effectPanel.setBounds(0, 0, 700, 35)
effectPanel.background = Color(18, 169, 212)
effectPanel.setLayout(None)
effectPanel.add(btn_open)
effectPanel.add(btn_save)
effectPanel.add(mnu_bar)

toolPanel = JPanel()
toolPanel.setBounds(0, 42, 700, 120)
toolPanel.setLayout(None)
toolPanel.add(btn_root)
toolPanel.add(lbl_level)
toolPanel.add(btn_plus)
toolPanel.add(txt_level)
toolPanel.add(btn_subtract)
# ------------------------------ END -----------------------------
app.add(effectPanel)
app.add(toolPanel)
app.visible = True