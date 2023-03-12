# bug-free-octo-winner
import math

def aire_heron(a_, b_, c_):
    s = (a_ + b_ + c_)/2
    return math.sqrt(s*(s-a_)*(s-b_)*(s-c_))
def tetrahedron_radius(WX, WY, WZ, XY, XZ, YZ):
    a = WX**2
    b = WY**2
    c = WZ**2
    d = XY**2
    e = XZ**2
    f = YZ**2
    
    D = a + b - d
    E = b + c - f
    F = a + c - e
    
    P = 4*a*b*c
    Q = (a*(E**2)) + (b*(F**2)) + (c*(D**2))
    R = D*E*F
    
    A = aire_heron(WX,WY,XY) + aire_heron(WX,WZ,XZ) + aire_heron(WY,WZ,YZ) + aire_heron(XY,XZ,YZ)
    
    volume = (math.sqrt(P - Q + R))/12
    return (3*volume)/A
t = int(input().strip())
for i in range(t):
    WX, WY, WZ, XY, XZ, YZ = [int(x) for x in input().split()]
    print("%.4f" % tetrahedron_radius(WX, WY, WZ, XY, XZ, YZ))
