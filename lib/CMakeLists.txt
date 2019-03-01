SET( cpp_files 
	"decode.c"
	"identify.c"
	"quirc.c"
	"version_db.c"
	)
SET( h_files_public
	"quirc.h"
	)
SET( h_files_private
	"quirc_internal.h"
	)

ADD_LIBRARY( quirc_shared SHARED ${cpp_files} ${h_files_public} ${h_files_private} )
ADD_LIBRARY( quirc_static STATIC ${cpp_files} ${h_files_public} ${h_files_private} )

SET_TARGET_PROPERTIES( quirc_shared quirc_static 
	PROPERTIES 
		LIBRARY_OUTPUT_NAME quirc
		ARCHIVE_OUTPUT_NAME quirc
	)

INSTALL( TARGETS quirc_shared quirc_static 
	ARCHIVE DESTINATION lib/
	LIBRARY DESTINATION lib/
	)

INSTALL( FILES ${h_files_public} DESTINATION include/ )
