# Use the official Microsoft SQL Server image from Docker Hub
FROM mcr.microsoft.com/mssql/server:2019-latest

# Set environment variables
ENV ACCEPT_EULA=Y
ENV SA_PASSWORD=!root2024
ENV MSSQL_PID=Express

# Expose SQL Server port
EXPOSE 1433

# Start SQL Server when the container starts
CMD ["/opt/mssql/bin/sqlservr"]
