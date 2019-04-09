CXXFLAGS = -g -Wall -std=c++11 $(VERBOSE) $(DEBUG)
LDFLAGS = -L/usr/local/opt/openssl/lib # -I/usr/local/opt/openssl/include
SSL = -lssl -lcrypto

all: client server
v: 
	@echo "Notice: certificates and messages will show"
	@make all VERBOSE=-DVERBOSE --no-print-directory 
	
# Executable 
client: client.o cmdCharDef.o util.h
	@echo "Linking client..."
	@g++ -o $@ $(CXXFLAGS) client.o cmdCharDef.o $(LDFLAGS) $(SSL)

server: server.cpp server.h ThreadPool.h util.h
	@echo "Building server..."
	@g++ -o $@ $(CXXFLAGS) server.cpp $(LDFLAGS) $(SSL)

# Object files
client.o: client.cpp client.h cmdParser.h util.h
	@echo "Building client..."
	@g++ -c $(CXXFLAGS) client.cpp $(LDFLAGS)

cmdCharDef.o: cmdCharDef.cpp cmdParser.h
	@echo "Building cmdCharDef..."
	@g++ -c $(CXXFLAGS) cmdCharDef.cpp

clean:
	@echo "Cleaning..."
	@rm -f *.o client server
	@rm -r -f *.dSYM
