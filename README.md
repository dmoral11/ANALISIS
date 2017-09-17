# ANALISIS
# ANALISIS
# -*- coding: utf-8 -*-
"""
Editor de Spyder

Este es un archivo temporal
"""
import numpy as np

#Este es el programa para cerchas
#Datos de entrada

Nn = 6
Ne = 9

MGL = np.array([[1,2,3,4],[3,4,11,12],[10,9,7,8],[7,8,5,6],[10,9,1,2],[1,2,7,8],[3,4,7,8],[7,8,11,12],[11,12,5,6]])
MA = np.array([[700],[700],[700],[700],[700],[700],[700],[700],[700]])
ME = np.array([[200],[200],[200],[200],[200],[200],[200],[200],[200]])
MC1 = np.array([[1.5,0,3,0],[3,0,4.5,0],[0,2.5,3,2.5],[3,2.5,6,2.5],[0,2.5,1.5,0],[1.5,0,3,2.5],[3,0,3,2.5],[3,2.5,4.5,0],[4.5,0,6,2.5]])
MC = MC1*1000
ML = np.zeros((Ne,1))

i = 0
for i in range(Ne):
    ML[i,0] = ((MC[i,2]-MC[i,0])**2 + (MC[i,3]-MC[i,1])**2)**0.5
    
MAL = np.zeros(((Ne,4,4)))

i = 0
for i in range(Ne):
    MAL[i,0,0] = (MA[i,0] * ME[i,0])/ML[i,0]
    MAL[i,0,2] = -MAL[i,0,0]
    MAL[i,2,0] = -MAL[i,0,0]
    MAL[i,2,2] = MAL[i,0,0]    
    
MAT = np.zeros(((Ne,4,4)))

i = 0
for i in range(Ne):
    MAT[i,0,0] = (MC[i,2]-MC[i,0])/ML[i,0]
    MAT[i,1,0] = (MC[i,3]-MC[i,1])/ML[i,0]
    MAT[i,2,2] = MAT[i,0,0]
    MAT[i,3,2] = MAT[i,1,0]
    
MAG = np.zeros(((Ne,4,4)))
