OPENCV_LIBPATH=/usr/local/lib
OPENCV_INCLUDEPATH=/usr/local/include
OPENCV_LIBS=-lopencv_core -lopencv_imgproc -lopencv_highgui

CUDA_INCLUDEPATH=/usr/local/cuda/include
CUDA_LIBPATH=/usr/local/cuda/lib
CUDA_LIBS=-lcudart

NVCC=/Developer/NVIDIA/CUDA-5.0/bin/nvcc
NVCC_OPTS=-O3 -Xcompiler -Wall -Xcompiler -Wextra -m64


GCC_OPTS=-O3 -Wall -Wextra -m64

student: compare main.o student_func.o Makefile
	$(NVCC) -o hw main.o student_func.o -L $(OPENCV_LIBPATH) $(OPENCV_LIBS) $(NVCC_OPTS)

main.o: main.cpp timer.h utils.h HW1.cpp
	g++ -c main.cpp $(GCC_OPTS) -I $(CUDA_INCLUDEPATH) -I $(OPENCV_LIBPATH)

student_func.o: student_func.cu reference_calc.cpp utils.h
	$(NVCC) -c student_func.cu $(NVCC_OPTS)

compare: compare.cpp utils.h Makefile
	g++ -o compare compare.cpp -I $(OPENCV_INCLUDEPATH) -L $(OPENCV_LIBPATH) $(OPENCV_LIBS) $(GCC_OPTS) -I $(CUDA_INCLUDEPATH)

clean:
	rm -f *.o *.png hw compare
