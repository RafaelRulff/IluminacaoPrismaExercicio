# IluminacaoPrismaExercicio

float ax, ay, dx, dy, dz;

float color[3] = {0.1, 0.6, 0.1 };

float v[8][3] = { 

    -1,  1, -1, 
    
     1,  1, -1, 
     
     1, -1, -1, 
     
    -1, -1, -1, 
    
    -1,  1,  1, 
    
    -1, -1,  1, 
    
     1, -1,  1, 
     
     1,  1,  1 
};

float norm[6][3] = { 

    0,  0, -1,
    
    0,  0,  1, 
    
   -1,  0,  0, 
   
    1,  0,  0, 
    
    0,  1,  0, 
    
    0, -1,  0 
};

int idx[6][4] =

{

0, 1, 2, 3, // Rear

4, 5, 6, 7, // Front

0, 3, 5, 4, // Left

7, 6, 2, 1, // Right

0, 4, 7, 1, // Top

5, 3, 2, 6, // Bottom

};

 (void) prepareOpenGL {

    [super prepareOpenGL];

    glEnable(GL_LIGHTING);
    
    glEnable(GL_LIGHT0);
    
    glEnable(GL_COLOR_MATERIAL);
    
    glShadeModel(GL_SMOOTH);
}


 (void) drawRect:(NSRect)rect {

    [super drawRect:rect];

    glClearColor(1, 1, 1, 0);
    
    glClear(GL_COLOR_BUFFER_BIT);

    glMatrixMode(GL_MODELVIEW);
    
    glLoadIdentity();

    glTranslatef(dx, dy, dz);
    
    glRotatef(ay, 0, 1, 0);
    
    glRotatef(ax, 1, 0, 0);

    glColor3fv(color);
    
    glBegin(GL_QUADS);

    for (int i = 0; i < 6; i++) {
    
        glNormal3fv(norm[i]);
        
        for (int j = 0; j < 4; j++)
        
            glVertex3fv(v[idx[i][j]]);
            
       }
   glEnd();
   
   glFlush();
   
}
