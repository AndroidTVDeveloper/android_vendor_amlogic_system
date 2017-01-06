libge2d user guide
API:
int ge2d_open(void);
int ge2d_close(int fd);
int ge2d_process(int fd,aml_ge2d_info_t *pge2dinfo);


typedef struct aml_ge2d_info {
    unsigned int offset;
    unsigned int blend_mode;
    GE2DOP ge2d_op;
    buffer_info_t src_info[2];
    buffer_info_t dst_info;
    unsigned int color;
    unsigned int gl_alpha;
} aml_ge2d_info_t;
�����ݽṹ�������£�
unsigned int offset�� 		osd��y_offset��
unsigned int blend_mode��	blend_mode ֻ��blend������Ч��
unsigned int color��        Ŀǰֻ��fillrectangle��Ч��
GE2DOP ge2d_op��            ge2d֧�ֵĲ���
ge2d֧�ֵĲ�����
    AML_GE2D_FILLRECTANGLE,
    AML_GE2D_BLEND,
    AML_GE2D_STRETCHBLIT,
    AML_GE2D_BLIT,

typedef struct buffer_info {
    unsigned int memtype;
    char* vaddr;
    unsigned long paddr;
    unsigned int canvas_w;
    unsigned int canvas_h;
    rectangle_t rect;
    int format;
    unsigned int rotation;
} buffer_info_t;
�����ݽṹ�������£�
memtype�� 				�����mem alloc,����Ϊ:CANVAS_ALLOC
						���ʹ��osd,����Ϊ��CANVAS_OSD0/CANVAS_OSD1
char* vaddr�� 			���for debug
unsigned long paddr;	�����mem alloc,����дmem phy addr
						���ʹ��osd,���裬kernel�����л�ȡ��
unsigned int canvas_w;						
unsigned int canvas_h;  �����mem alloc,����дcanvas width,height, related to mem size.
						���ʹ��osd,���裬kernel�����л�ȡ��
int format;				�����mem alloc,����дpixel format
						���ʹ��osd,���裬kernel�����л�ȡ��
rectangle_t rect;       ����ʵ�������дrect�������
unsigned int rotation;  ����Ϊ0/90/180/270��

1.  AML_GE2D_FILLRECTANGLE ��Ҫ���õ����ݽṹ�������£�
��Ҫ����:
src_info[0]; 
dst_info;
color;
offset;

2.AML_GE2D_BLEND��Ҫ���õ����ݽṹ�������£�
��Ҫ����:
src_info[0];
src_info[1];
dst_info;
blend_mode;
offset;
    
3.AML_GE2D_STRETCHBLIT ��Ҫ���õ����ݽṹ�������£�
��Ҫ����:
src_info[0];
dst_info;
offset;

3.AML_GE2D_BLIT ��Ҫ���õ����ݽṹ�������£�
��Ҫ����:
src_info[0];
dst_info;
offset;



